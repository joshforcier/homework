<template>
    <div class="javascript">
        <div class="dropdown__container">
            <div class="dropdown__label">Your Gains</div>
            <div
                @click="toggleYourGains()"
                class="dropdown__toggle"
            >
                {{ displayGains(yourGainMin, yourGainMax) }}
                <span class="dropdown__chevron">
                    <img src="../assets/down-chevron.svg" alt="down chevron" height="10" width="10">
                </span>
            </div>
            <div
                class="slider__container"
                v-if="showYourSlider"
            >
                <span class="slider__values__low">{{ yourGainMin }}%</span>
                <input
                    class="slider__range"
                    v-model="yourGainMin"
                    min="0"
                    max="10"
                    step="0.1"
                    type="range"
                    aria-label="Scale"
                    @change="onstateChanged(yourGainMin, yourGainMax, theirGainMin, theirGainMax)"
                >
                <span class="slider__values__high">{{ yourGainMax }}%</span>
                <input
                    class="slider__range"
                    v-model="yourGainMax"
                    min="0"
                    max="10"
                    step="0.1"
                    type="range"
                    aria-label="Scale"
                    @change="onstateChanged(yourGainMin, yourGainMax, theirGainMin, theirGainMax)"
                >
            </div>
        </div>

        <div class="dropdown__container">
            <div class="dropdown__label">Their Gains</div>
            <div
                @click="toggleTheirGains()"
                class="dropdown__toggle"
            >
                {{ displayGains(theirGainMin, theirGainMax) }}
                <span class="dropdown__chevron">
                    <img src="../assets/down-chevron.svg" alt="down chevron" height="10" width="10">
                </span>
            </div>

            <div
                class="slider__container"
                v-if="showTheirSlider"
            >
                <span class="slider__values__low">{{ theirGainMin }}%</span>
                <input
                    class="slider__range2"
                    v-model="theirGainMin"
                    min="0"
                    max="10"
                    step="0.1"
                    type="range"
                    aria-label="Scale"
                    @change="onstateChanged(yourGainMin, yourGainMax, theirGainMin, theirGainMax)"
                >
                <span class="slider__values__high">{{ theirGainMax }}%</span>
                <input
                    class="slider__range2"
                    v-model="theirGainMax"
                    min="0"
                    max="10"
                    step="0.1"
                    type="range"
                    aria-label="Scale"
                    @change="onstateChanged(yourGainMin, yourGainMax, theirGainMin, theirGainMax)"
                >
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Javascript',
    data() {
        return {
            showYourSlider: false,
            showTheirSlider: false,
            yourGainMin: 0.5,
            yourGainMax: 8,
            theirGainMin: 0.5,
            theirGainMax: 8,
        }
    },
    props: {
        msg: String,
    },
    methods: {
        toggleYourGains() {
            this.showYourSlider = !this.showYourSlider;
        },
        toggleTheirGains() {
            this.showTheirSlider = !this.showTheirSlider;
        },
        onstateChanged(yourGainMin, yourGainMax, theirGainMin, theirGainMax) {
            // eslint-disable-next-line no-console
            console.log(yourGainMin, yourGainMax, theirGainMin, theirGainMax);
        },
        displayGains(min, max) {
            return (min == 0 && max == 10)
                ? "All gains"
                : min + " to " + max + "%";
        },
    },
}
</script>

<style lang="scss">
.javascript {
    margin: auto auto 10% auto ;
    width: 25%;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 5%;
}

.dropdown__container {
    width: 300px;
}

.dropdown__toggle {
    border: solid #D3D3D3 1px;
    width: 100px;
}

.dropdown__label {
    text-align: left;
    width: 100px;
}

.slider__container {
    border: solid #D3D3D3 1px;
    height: 30px;
}

.slider__values__low {
    margin: 10px;
    float: left;
}

.slider__values__high {
    margin: 10px;
    float: right;
}

// Start https://codepen.io/rendykstan/pen/VLqZGO
@mixin slider__container($width, $height, $input-top, $input-bg-color, $input-thumb-color, $float:none, $input-height:20px, $input-border-radius:14px) {
    position: relative;
    width: $width;
    height: $height;
    float: $float;
    text-align: center;
    
    input[type="range"] {
        pointer-events: none;
        position: absolute;
        -webkit-appearance: none;
        -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
        border: none;
        border-radius: $input-border-radius;
        background: $input-bg-color;
        box-shadow: inset 0 1px 0 0 darken($input-bg-color,15%), inset 0 -1px 0 0 darken($input-bg-color,10%);
        -webkit-box-shadow: inset 0 1px 0 0 darken($input-bg-color,15%), inset 0 -1px 0 0 darken($input-bg-color,10%);
        left: 12px;
        top: $input-top;
        width: $width;
        outline: none;
        height: 10px;
    }

    input[type="range"]::-webkit-slider-thumb {
        pointer-events: all;
        position: relative;
        z-index: 1;
        outline: 0;
        -webkit-appearance: none;
        width: 30px;
        height: 30px;
        border: none;
        box-shadow: inset 0 1px 0 0 darken($input-bg-color,15%), inset 0 -1px 0 0 darken($input-bg-color,10%);
        border-radius: $input-border-radius;
        background-image: -webkit-gradient(linear, left top, left bottom, color-stop(0%, lighten($input-thumb-color,60%)), color-stop(100%, $input-thumb-color)); /* android <= 2.2 */
        background-image: -webkit-linear-gradient(top , lighten($input-thumb-color,60%) 0, $input-thumb-color 100%); /* older mobile safari and android > 2.2 */;
        background-image: linear-gradient(to bottom, lighten($input-thumb-color,60%) 0, $input-thumb-color 100%); /* W3C */
    }
  
    input[type="range"]::-moz-range-thumb {
        pointer-events: all;
        position: relative;
        z-index: 10;
        -moz-appearance: none;
        width: $input-height;
        height: $input-height;
        border: none;
        border-radius: $input-border-radius;
        background-image: linear-gradient(to bottom, lighten($input-thumb-color,60%) 0, $input-thumb-color 100%); /* W3C */
    }

    input[type="range"]::-ms-thumb {
        pointer-events: all;
        position: relative;
        z-index: 10;
        -ms-appearance: none;
        width: $input-height;
        height: $input-height;
        border-radius: $input-border-radius;
        border: 0;
        background-image: linear-gradient(to bottom, lighten($input-thumb-color,60%) 0, $input-thumb-color 100%); /* W3C */
    }

    input[type=range]::-moz-range-track {
        position: relative;
        z-index: -1;
        background-color: rgba(0, 0, 0, 1);
        border: 0;
    }

    input[type=range]:last-of-type::-moz-range-track {
        -moz-appearance: none;
        background: none transparent;
        border: 0;
    }

    input[type=range]::-moz-focus-outer {
        border: 0;
    }
}

div.slider__container {
    @include slider__container(90%, 100px, 50px, #F1EFEF, #F1EFEF, left);
}
// End https://codepen.io/rendykstan/pen/VLqZGO
</style>
