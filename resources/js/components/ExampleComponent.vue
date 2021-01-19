<template>
    <div class="container" @mousemove="audio('/audio/2.mp3')">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>
                    <div class="card-body">
                        This is a software to make an notification on a web Application using Laravel WebSocket by Hridoy (Me)

                        Please move your mouse on this area (container)
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        mounted() {
            Echo.join('test')
                .here((users) => {
                    this.audio('/audio/sleep away.mp3')
                })
                .joining((user) => {
                    this.audio('/audio/2.mp3')
                })
                .leaving((user) => {
                    this.audio('/audio/2.mp3')
                });
        },
        methods:{
            audio(sound){
                if(sound) {
                    var audio = new Audio(sound);
                    audio.play();
                }
            }
        }
    }
</script>
