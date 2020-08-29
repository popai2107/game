<template>
<div>
    <img :src="Logo" width="300" height="160" class="img-fluid mx-auto">
    <br />
    <br />
    <button v-on:click="randomHero" class="btn btn-success mb-4">START</button>
    <br />
    <button v-on:click="attack" class="btn btn-danger mb-4">Attack</button>
    <button v-on:click="special" class="btn btn-warning mb-4">SpecialAttack</button>
    <br />
    <br />
    
    <div class="contianer">
        <div class="row">
            <div class="col-4">
                Name : {{NameHero}}
                <br />
                <img :src="ImgHero" :height="HPHero" class="mx-auto" />
                <br>
                HP : {{HPHero}}
                <br>
                <img v-bind:style="{width : HPHero + 'px'}" :src="BloodHero" alt height="10px" class=" mx-auto" />
            </div>
            
            <div class="col-4">
                Name : {{NameMonster}}
                <br />
                <img :src="ImgMonster" :height="HPMonster" class="mx-auto" />
                <br>
                HP : {{HPMonster}}
                <br>
                <img v-bind:style="{width : HPMonster + 'px'}" :src="BloodMonster" alt height="10px" class=" mx-auto" />
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            BloodHero: "https://cdn.discordapp.com/attachments/746260527235334237/748860632693997595/BloodHero.png",
            BloodMonster: "https://cdn.discordapp.com/attachments/746260527235334237/748860627560300544/BloodMonster.png",
            Hero: "",
            Monster: "",
            NameHero: "",
            NameMonster: "",
            HPHero: "",
            HPMonster: "",
            SPATKHero: "",
            SPATKMonster: "",
            ATKHero: "",
            ATKMonster: "",
            Logo: "http://www.pngall.com/wp-content/uploads/4/Marvel-Logo.png",
          

            //เลือกผู้เล่น
            player: [{
                name: 'Iron Man',
                hp: 800,
                image: 'http://www.pngall.com/wp-content/uploads/4/Marvel-Avengers-PNG.png'
               
            }, {
                name: 'Captain America',
                hp: 700,
                image: 'http://www.pngall.com/wp-content/uploads/4/Marvel-PNG-Transparent-HD-Photo.png' 
                
            }, {
                name: 'Black Widow',
                hp: 850,
                image: 'http://www.pngall.com/wp-content/uploads/4/Marvel-PNG-Pic.png'
            }, {
                name: 'Captain Marvel',
                hp: 875,
                image: 'http://www.pngall.com/wp-content/uploads/4/Marvel-PNG-Image-File.png' 
            }, {
                name: 'Vision',
                hp: 800,
                image: 'http://www.pngall.com/wp-content/uploads/4/Marvel-PNG-Clipart.png'
            }, {
                name: 'Spiderman',
                hp: 850,
                image: 'http://www.pngall.com/wp-content/uploads/4/Marvel-PNG-Image-HD.png'
            }],
            //เลือกมอนสเตอร์
            monster: [{
                name: 'Thanos',
                hp: 850,
                image: 'http://www.pngmart.com/files/9/Marvel-Thanos-PNG-Free-Download.png'
            }, {
                name: 'Ultron',
                hp: 800,
                image: 'http://www.pngmart.com/files/4/Ultron-PNG-Pic.png'
            }, {
                name: 'Magneto',
                hp: 800,
                image: 'http://www.pngall.com/wp-content/uploads/2016/06/Magneto-Free-PNG-Image.png'
            }, {
                name: 'Loki',
                hp: 850,
                image: 'http://www.pngall.com/wp-content/uploads/2016/05/Loki-High-Quality-PNG.png'
            }, {
                name: 'The Green Goblin',
                hp: 700,
                image: 'http://www.pngall.com/wp-content/uploads/4/Flying-Green-Goblin-PNG-Free-Download.png'
            }, {
                name: 'Doctor Doom',
                hp: 900,
                image: 'https://cartoon.mthai.com/app/uploads/2013/04/182.jpg'
            }]
        }
    },
    methods: {
        randomHero: function () {
            this.Hero = Math.max(Math.floor(Math.random() * this.player.length));
            this.Monster = Math.max(Math.floor(Math.random() * this.monster.length));
            this.HPHero = this.player[this.Hero].hp
            this.HPMonster = this.monster[this.Monster].hp
            this.NameHero = this.player[this.Hero].name
            this.NameMonster = this.monster[this.Monster].name
            this.ImgHero = this.player[this.Hero].image
            this.ImgMonster = this.monster[this.Monster].image
            
        },
        attack: function () {
            this.ATKHero = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            this.ATKMonster = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.ATKMonster;
            }
            if (this.HPMonster != 0 && this.HPHero != 0) {
                this.HPMonster -= this.ATKHero;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
              
            }
        },
        special: function () {
            this.SPATKHero = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            this.SPATKMonster = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPMonster -= this.SPATKHero;
            }
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.SPATKMonster;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
               // this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
               // this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
               // this.ImgLose = this.Lose;
            }
        },
        
    }
}
</script>

<style>
body {
    font-family: 'Russo One', sans-serif;
}
</style>