<template>
    <div style="display:block;text-align:center">
        <div :id="id">
            <p>To play this game, please, download the latest Flash player!</p>
            <br>
            <a href="http://www.adobe.com/go/getflashplayer">
                <img
                    src="//www.adobe.com/images/shared/download_buttons/get_adobe_flash_player.png"
                    alt="Get Adobe Flash player"
                >
            </a>
        </div>
    </div>
</template>

<script >
import { Prop, Watch, Vue, Component } from "vue-property-decorator";
import swfobject from "swfobject";

@Component({
    props: {
        propMessage: String
    }
})
export default class Home extends Vue {
    @Prop({ name: "url" })
    url;

    @Prop({ name: "system", default: "sega" })
    system;

    @Prop({ name: "emulator", default: "/flash/Nesbox.swf" })
    emulator;

    id;

    guidGenerator() {
        var S4 = function() {
            return (((1 + Math.random()) * 0x10000) | 0)
                .toString(16)
                .substring(1);
        };
        return (
            "_" +
            (S4() +
                S4() +
                "-" +
                S4() +
                "-" +
                S4() +
                "-" +
                S4() +
                "-" +
                S4() +
                S4() +
                S4())
        );
    }

    @Watch("url")
    urlChanged() {
        this.embed(600, 448);
    }

    created() {
        this.id = this.guidGenerator();
        window.resizeOwnEmulator = (width, height) => {
            let el = document.getElementById(this.id);
            el.style.width = width;
            el.style.height = height;
        };
    }

    mounted() {
        this.embed(600, 448);
    }
    embed(width, height) {
        var emulator = document.getElementById(this.id);

        if (emulator) {
            var flashvars = {
                system: this.system,
                url: this.url
            };
            var params = {};
            var attributes = {};

            params.allowscriptaccess = "sameDomain";
            params.allowFullScreen = "true";
            params.allowFullScreenInteractive = "true";
            swfobject.embedSWF(
                "/flash/Nesbox.swf",
                this.id,
                width + "",
                height + "",
                "11.2.0",
                "flash/expressInstall.swf",
                flashvars,
                params,
                attributes
            );
        }
    }
}
</script>
<style>
</style>