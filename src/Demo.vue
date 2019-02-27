<template>
    <div>
        <h1>Test</h1>
        <div style="width:200px;height:56px;background-color:black" @click="doit"></div>
        <game-player url="/my.SMD"></game-player>
    </div>
</template>

<script>
import { Prop, Watch, Vue, Component } from "vue-property-decorator";
import GamePlayer from "./GamePlayer";

@Component({
    props: {
        propMessage: String
    },
    components: {
        GamePlayer
    }
})
export default class Demo extends Vue {
    gameUrl = null;
    doit() {
        this.gameUrl = "my.SMD";
    }
}
</script>

<style>
</style>