<template>
    <div class="css">
        <div class="css__header">
            <img
                class="css__hotIcon"
                src="../assets/hot-icon@3x.png"
                alt="hot icon"
            >
            <div class="css__title">HOT MATCHUPS</div>
            <span>
                <img
                    class="css__chevron"
                    src="../assets/left-chevron.svg"
                    alt="left chevron"
                >
            </span>
            <span>
                <img
                    class="css__chevron"
                    src="../assets/right-chevron.svg"
                    alt="right chevron"
                >
            </span>
        </div>

        <div class="css__main">
            <div class="css__matchup">
                <div>
                    <div class="css__matchup__team">OAK</div>
                    <div>2-1-1</div>
                </div>
                <div class="css__matchup__at">at</div>
                <div>
                    <div class="css__matchup__team">DET</div>
                    <div>2-1-1</div>
                </div>
                <div class="css__matchup__time">Sun 4pm</div>
            </div>
            <div class="css__main__bottomBorder"></div>

            <div class="css__consensus">
                <div class="css__consensus__container">
                    <img
                        class="css__consensus__awayImg"
                        src="../assets/green_circle.png"
                        alt="pie graph"
                    >
                    <div
                        class="css__consensus__percentage"
                        :class="{'css__consensus__percentage--majority': isAwayMajority}"
                    >
                        {{ awayPercentage }}%
                    </div>
                </div>
                <div class="css__consensus__label">Expert Consensus</div>
                <div class="css__consensus__container">
                    <img
                        class="css__consensus__homeImg"
                        src="../assets/gray_circle.png"
                        alt="pie graph"
                    >
                    <div
                        class="css__consensus__percentage"
                        :class="{'css__consensus__percentage--majority': !isAwayMajority}"
                    >
                        {{ homePercentage }}%
                    </div>
                </div>
            </div>
        </div>

        <div class="css__footer">
            <a href="#" class="css__footer__link">View Matchup</a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CSS',
    data() {
        return {
            homePercentage: 40,
            awayPercentage: 60,
        }
    },
    computed: {
        isAwayMajority() {
            return (this.awayPercentage > this.homePercentage);
        },
    },
}
</script>


<style lang="scss">
.css {
    border: solid #D3D3D3 1px;
    border-radius: 5px;
    width: 400px;
    height: 400px;
    margin: auto;
}

.css__header {
    display: grid;
    grid-template-columns: 10% 70% 10% 10%;
    padding: 5%;
    font-weight: bold;
    font-size: 20px;
    height: 25px;
    border-bottom: solid #D3D3D3 1px;

    .css__hotIcon {
        width: 20px;
    }

    .css__chevron {
        width: 15px;
    }

    .css__title {
        display: flex;
        align-items: center;
    }
}

.css__main {
    .css__matchup {
        margin-top: 10%;
        display: grid;
        grid-template-columns: 45% 10% 45%;
        grid-row: 1;

        .css__matchup__team {
            font-weight: bold;
            font-size: 32px;
        }

        .css__matchup__at {
            margin: auto;
            color: #585858;
        }
    }

    .css__matchup__time {
        padding: 5% 0% 5% 0%;
        grid-column-end: span 3;
        color: #585858;
    }

    .css__main__bottomBorder {
        width: 75%;
        margin: auto;
        border-bottom: solid #D3D3D3 1px;
    }

    .css__consensus {
        margin: 10% 0 6%;
        display: grid;
        grid-template-columns: 40% 20% 40%;

        .css__consensus__label {
            margin: auto;
        }

        .css__consensus__container {
            position: relative;

            .css__consensus__percentage {
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%, -50%);
                font-weight: bold;
                font-size: 28px;
                color: #909090;

                &--majority {
                    color: #426B17;
                }
            }
        }
    }
}

.css__footer {
    border-top: solid #D3D3D3 1px;

    .css__footer__link {
        text-decoration: none;
    }
}
</style>
