<template>
    <section class="container">
        <article v-if="!error" :class="{background:true,sunset:(hourFormatter>=19 && hourFormatter<=20), sunrise:(hourFormatter>=5 && hourFormatter<=7), night:hourFormatter>=21 || hourFormatter<=4,day:(hourFormatter>=8 && hourFormatter<=18) }">
            <aside>
                <h3>{{weatherData.location?.name}} - {{weatherData.location?.region}} - {{weatherData.location?.country}} </h3>       
                <h2 v-if="temp=='' || temp=='C'">{{weatherData.current?.temp_c}}°C</h2>
                <h2 v-if="temp=='F'">{{weatherData.current?.temp_f}}°F</h2>
                <h5>{{weatherData.current?.condition.text}}</h5>
                <img :src="weatherData.current?.condition.icon" alt="">
                <h6><i class="fa-solid fa-temperature-quarter"></i> UV Index: {{weatherData.current?.uv}}</h6>
            </aside>
            <aside>
                <p>{{this.weatherData.location?.localtime}}</p>
            </aside>

        </article>
        <article v-else class="background">
            <div class="error-container">
            <img class="gif" src="/src/assets/img/cloud.gif" alt="cloud">
            <p class="text">We could not find the city <span>{{city}}</span></p>
            </div>
        </article>
    </section>
</template>


<script>
    export default {
    name:'CurrentData',
    props:{
        city:String,
        temp:String
    },
    data() {

        return {
            // api: "/src/services/currentResponse.json",
            api: `http://api.weatherapi.com/v1/current.json?key=408f7a5f3969465998531549232308&q=${this.city}&aqi=no`,
            weatherData:{},
            dateFormat:"",
            hour:"",
            error:false
        }
        
    },

    watch:{
        city(newV,oldV) {
            this.getData(newV);
            this.$emit('arrayCities',this.weatherData);
        }
    },  
    methods:{
        
        async getData(cities="Vancouver"){
            try{
                 await fetch(`http://api.weatherapi.com/v1/current.json?key=2a14e50aa2e84b31b68232912232806&q=${cities}&aqi=no`).then(res=>{
                    if(!res.ok) {
                        this.error=true;

                        return Promise.reject(response);
                    }else {
                        this.error=false;
                    return res.json()

                    }
                 }).then(data=>this.weatherData=data);
                 console.log(this.weatherData)
                //  this.dateFormat = new Date(this.weatherData.location?.localtime_epoch*1000).toLocaleString('en-US',{ weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })
                //  this.hour=new Date(this.weatherData.location?.localtime_epoch*1000).getHours();
                this.$emit("dataWeather",this.weatherData)
               
            } catch(e) {
                // console.log(e);
                console.log('Ciudad no encontrada')
            }
        }

    },
    computed:{
        dateFormatter:function(){
            let dates = new Date(this.weatherData.location?.localtime_epoch*1000).toLocaleString('en-US',{ weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' });
            return dates
        },
        hourFormatter:function(){
            let hours = Number(this.weatherData.location?.localtime.split(' ')[1].slice(0,2));
            if(!hours) {
                hours = Number(this.weatherData.location?.localtime.split(' ')[1].slice(0,1));
            }
            this.$emit('hourDay',hours);
            return hours;
        }
    },
    created(){
        this.getData();
    }
}
</script>
<style scoped>
.container {
padding: 4vh 7vh 7vh 7vh;
display: flex;
justify-content: center;
}

.container article {
    transition: .4s;
}

.container article:hover {
    transform: scale(1.01);
}
.error-container {
    color: black;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;

}
.error-container p {
    font-size: 35px;
}
.error-container span {
    font-weight: bold;
}
.background {
    background-position: top;
    padding: 3vh;
    color: white;
    background-size: cover;
    background-repeat: no-repeat;
    /* background-image: url("https://cdn.vox-cdn.com/thumbor/R4HOj89cekaEOkDW2hOiz8QnjK4=/0x0:2560x1440/1400x1050/filters:focal(1280x720:1281x721)/cdn.vox-cdn.com/uploads/chorus_asset/file/21857937/Land_Sea_UpcomingProject_TeaserImage.png"); */
    /* background-image: linear-gradient(to bottom,#FFC26F,#C38154,#884A39); */
    height: fit-content;
    width: 90%;
    border-radius: 15px;
    display: flex;
    justify-content: space-between;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

.sunset {
    background-image: url("https://149362454.v2.pressablecdn.com/previously/wp-content/uploads/sites/5/2015/02/b04_QuarterPipe.png");
}

.sunrise {
    background-image: url("https://cdn.vox-cdn.com/thumbor/R4HOj89cekaEOkDW2hOiz8QnjK4=/0x0:2560x1440/1400x1050/filters:focal(1280x720:1281x721)/cdn.vox-cdn.com/uploads/chorus_asset/file/21857937/Land_Sea_UpcomingProject_TeaserImage.png");

}
.night {
    background-image: url("https://i.pinimg.com/originals/a2/48/92/a24892f0b14a4a847a63139741de6fbf.jpg");
}
.day {
    background-image: url("https://i.pinimg.com/originals/f1/3d/a2/f13da27bb30ffbd69cb504d52767e1b9.jpg");
}

.gif {
    width: 50vh;
    height: 50vh;
}

aside {
    display: flex;
    flex-direction: column;

}

aside img {
    width: 12vh;
    height: 12vh;
}
h3,h5 {
    color: white;
    font-size: 30px;
    font-weight: 400;
}
h2 {
    color: white;
    font-size: 135px;

}
h6 {
    font-size: 20px;

}
p {
    font-size: 25px;

}
.fade-enter-active {
  transition: opacity 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>