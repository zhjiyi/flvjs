<!--
 * @Descripttion: 
 * @version: 
 * @Author: liuyq
 * @Date: 2022-07-04 18:26:16
 * @LastEditors: zhoujy
 * @LastEditTime: 2022-07-04 18:42:43
-->
<template>
    <video ref="video" autoplay>
        Your browser is too old which doesn't support HTML5 video.
    </video>
</template>
<script>
import flvjs from "flv.js"
export default {
    name: "flvModule",
    data() {
        return {
            src:"https://sample-videos.com/video123/flv/720/big_buck_bunny_720p_2mb.flv",
            flvPlayer:null,
        }
    },
    created() {
        this.$nextTick(() => {
            if (flvjs.isSupported()) {
                const flvPlayer = flvjs.createPlayer({
                    type: "flv",
                    isLive: true,
                    url: this.src,
                });
                flvPlayer.attachMediaElement(this.$refs.video);
                flvPlayer.load();
                flvPlayer.play();
                this.flvPlayer = flvPlayer;
            }
        });
    },
};
</script>