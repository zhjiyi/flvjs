<template>
    <div>
        <video controls id="videoEle" width="500" height="300" muted>
        </video>
    </div>

</template>

<script>
import flvjs from "flv.js"
import videoUrl from "../assets/video2.mp4"
export default {
    name: "HelloWorld",
    data() {
        return {
            src: require("../../static/vvas.flv"),
            flvPlayer: '',
        };
    },
    created() {
        
    },
    mounted() {
        if (flvjs.isSupported()) { 
            var timer = setTimeout(() => {
                var video = document.getElementById("videoEle");
                this.flvPlayer = flvjs.createPlayer({
                    type: "flv",
                    url: this.src,
                });
                console.log(this.flvPlayer);
                console.log(video)
                this.flvPlayer.attachMediaElement(video);
                this.flvPlayer.load();
                this.flvPlayer.play();
            }, 2000)
        }else {
            console.log('浏览器不支持flv')
        }
        

        // this.$nextTick(() => {
        //     var video = document.getElementById("video");
        //     this.flvPlayer.attachMediaElement(video);
        //     this.flvPlayer.load();
        // });
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
    font-weight: normal;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
