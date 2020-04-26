<template>
    <div id="app">
        <div class="row">
            <div
                class="col-4 cool"
                :style="{ backgroundImage: `url(${img_src})` }"
            ></div>
            <div class="col-8">
                <button
                    @click="changePhoto(1)"
                    type="button"
                    class="btn m-3 btn-primary"
                >
                    64 GB
                </button>
                <button
                    @click="changePhoto(2)"
                    type="button"
                    class="btn m-3 btn-primary"
                >
                    32 GB
                </button>
                <button
                    @click="changePhoto(3)"
                    type="button"
                    class="btn m-3 btn-primary"
                >
                    128 GB
                </button>
            </div>
        </div>
        <div class="row">
            <div class="col-4 price">
                {{ cost }}
            </div>
            <div v-if="avail && !limit" @click="putInCart" class="col-8">
                <button type="button" class="btn btn-success btn-lg btn-block">
                    PUT IN CART
                </button>
            </div>
            <div v-if="!avail || limit" class="col-8">
                <button type="button" class="btn btn-lg btn-danger" disabled>
                    OUT OF STOCK
                </button>
            </div>
        </div>
        <div class="row center">
            YOU HAVE {{ in_cart_no }} ITEMS IN THE CART
        </div>
    </div>
</template>

<script>
export default {
    name: "App",
    components: {},
    data() {
        return {
            img_src:
                "https://images.unsplash.com/photo-1512054502232-10a0a035d672?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=60",
            cost: "$500",
            avail: true,
            in_cart_no: 0,
            primary_color: "red",
            limit: false,
        };
    },
    methods: {
        changePhoto: function(value) {
            if (value == 1) {
                this.img_src =
                    "https://images.unsplash.com/photo-1586719065876-9b6b5ae9e91a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=60";
                this.cost = "$500";
            }
            if (value == 2) {
                this.img_src =
                    "https://images.unsplash.com/photo-1587834309224-b683f5f39e70?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=60";
                this.cost = "$300";
            }
            if (value == 3) {
                console.log("asdsd");
                this.img_src =
                    "https://images.unsplash.com/photo-1587870306141-4f19861e6c73?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=60";
                this.cost = "$600";
            }
        },
        putInCart() {
            if (this.in_cart_no < 3) {
                this.in_cart_no++;
            } else {
                this.limit = true;
                alert("YOU CAN NOT BUY ANYMORE OF THIS ITEM AT ONCE");
            }
        },
    },
};
</script>

<style>
* {
    box-sizing: border-box;
    margin: 0px;
    padding: 0px;
}

.cool {
    height: 50vh;
    background-repeat: no-repeat;
    background-size: cover;
}
.price {
    font-size: 3rem;
    border: 3px solid #8c7ae6;
}
.center {
    display: flex;
    flex-direction: row;
    justify-content: center;
}
</style>
