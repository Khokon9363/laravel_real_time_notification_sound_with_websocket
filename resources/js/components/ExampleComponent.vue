<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>
                    <div class="card-body">
                        This is a software to make an notification on a web Application using Laravel WebSocket by Hridoy (Me)
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
                    this.audio('/audio/SleepAway.mp3')
                })
                .joining((user) => {
                    console.log(user.name+' is joining');
                })
                .leaving((user) => {
                    console.log(user.name+' is leaving');
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
