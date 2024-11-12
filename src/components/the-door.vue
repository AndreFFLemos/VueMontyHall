<template>
  <div class="door-area">
    <div class="door-frame" :class="{selected: selected && !open}"> 
        <GiftBox v-if="open && hasGift"/>
    </div>
    <div class="door" :class="{open}" @click="selected = !selected">
        <div class="number" :class="{selected}">{{number}}</div>
        <div class="knob" :class="{selected}" @click="open=true"></div>
    </div>
  </div>
</template>
            
<script>
import GiftBox from './gift-box.vue';

export default {
name: 'TheDoor',
components: {GiftBox},
props: {
    number: {
        type:Number,
        required: true
    },
    hasGift: { 
        type: Boolean,
        default: false
    }
    },
    data () {
    return {
    open:false,
    selected: false,
    }
    },
//     methods: {
//     toggleDoor() {
//       this.selected = !this.selected;
//       if (this.hasGift) {
//         this.open = this.selected; // Abre a porta se tiver presente e estiver seleccionada
//       }
//     }
// }
}
</script>

<style>
:root {
    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
}

.door-area {
    position:relative;
    width:200px;
    height: 310px;
    border-bottom: 10px solid #aaa;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;
    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);

    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.door {
    position: absolute;
    top:5px;
    height: 295px ;
    width:170px ;
    background-color: chocolate;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

.door .knob {
    height:20px;
    width: 20px;
    border-radius: 10px;
    background-color: brown;
    align-self: flex-start;
    margin-top: 60px;
}

.door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}

.door .number .selected {
    color: yellow
}

.door .knob.selected {
    background-color: yellow;
}

.door.open {
    background-color: #0007;
}

.door.open .knob {
display: none;
}

.door.open .number {
    display: none;
}
</style>