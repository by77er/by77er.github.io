<template>
    <div id="maincont">
        <pre id='name'>{{ asciiart }}</pre>
        <transition name="show">
            <div v-if="showMain">
                <div class="text">
                    <pre class="text">- <a target="_blank" href="https://github.com/by77er">github</a> - <a target="_blank" href="https://repl.it/@by77er">repl.it</a> - <a target="_blank" href="https://www.hackthebox.eu/profile/3354">hackthebox</a> -</pre>
                    <br>
                    <p><span class="green">Heyo.</span></p>
                    <p>
                        It's me, by77er <span class="dim">(aka Bit)</span>. I program professionally and as a hobby, and I'm majoring in Computer Science at
                        <span class="red">$university</span>.
                    </p>
                    -
                    <p>
                        Though I'm primarily a programmer, I occasionally dabble in information security, design, and art.
                        I'm currently <span id="age" ref="age_el" class="red" v-on:click="showAge()">{{age}}</span> years old, and I've been programming for six to seven years now.
                        I do my best to stay busy with projects, and I'm always trying to learn something new.
                    </p>
                </div>
                <br>
                <div class="text">
                    <p><span class="green">Languages I know:</span></p>
                    <div class='flexc'>
                        <Lang v-for="item in languages" v-bind:key="item.name" v-bind:lang="item" :style="{'--theme-color': item.color, '--alt-color': item.alt || '#101011'}" class="language"></Lang>
                    </div>
                    <transition name="show">
                        <div id="lang_detail" v-if="langObject">
                            <fieldset>
                                <legend>{{langObject.name}}</legend>
                                <table>
                                    <tr>
                                        <td>Years of Experience: </td>
                                        <td>{{langObject.years}}</td>
                                    </tr>
                                </table>
                                <Tag v-for="item in langObject.subData" v-bind:key="item" v-bind:cont="item"></Tag>
                            </fieldset>
                        </div>
                    </transition>
                    <p><span class="green">My other skills:</span></p>
                    <div class='flexc'>
                        <Tag class="language" v-for="item in skills" v-bind:key="item" v-bind:cont="item"></Tag>
                    </div>
                </div>
                <br>
                <span class="text dim" id="footer">written by by77er with vue.js</span>
            </div>
        </transition>
    </div>
</template>

<script>
import Lang from './Lang';
import Tag from './Tag';
export default {
    name: "MainPage",
    components: {
        Lang,
        Tag
    },
    mounted() {
        let timer = 0;
        let count = 0;
        let target = art.length - 1;
        art.split('').forEach((i) => {
            count++;
            const _count = count;
            setTimeout(() => {
                this.asciiart = this.asciiart + i;
                if (_count === target) {
                    this.showMain = true;
                }
            }, timer);
            timer += 2;
        });
    },
    methods: {
        showAge() {
            this.$refs.age_el.className = 'green';
            // Hi. No, my full birthday isn't here.
            this.age = `~${String((new Date()).getFullYear()-2001)}`;
        },
        showLangDetail(lObject) {
            this.langObject = undefined;
            setTimeout(() => {this.langObject = lObject;}, 0);
        },
    },
    
    data() {
        return {
            asciiart: '',
            showMain: false,
            age: '$age',
            langObject: undefined,
            languages: [
                {
                    name: 'JavaScript',
                    color: '#f7e018',
                    years: 4,
                    subData: ['Node.js (backend)', 'Vue.js']
                },
                {
                    name: 'C',
                    color: '#477ce6',
                    alt: '#E8E7DD',
                    years: 3,
                    subData: []
                },
                {
                    name: 'Python',
                    color:  '#ffdd6d',
                    years: 5,
                    subData: []
                },
                {
                    name: 'Lua',
                    color: '#000080',
                    alt: '#E8E7DD', // base color
                    years: 6,
                    subData: []
                },
                {
                    name: 'Java',
                    color: '#e04d3b',
                    alt: '#E8E7DD',
                    years: 5,
                    subData: ['Minecraft Forge', 'Bukkit']
                },
                {
                    name: 'C++',
                    color: '#3571ad',
                    alt: '#E8E7DD',
                    years: 3,
                    subData: []
                },
                {
                    name: 'Elixir',
                    color: '#997bb1',
                    alt: '#E8E7DD',
                    years: 1,
                    subData: []
                },
                {
                    name: 'Rust',
                    color: '#ff9533',
                    years: 3,
                    subData: []
                },
                {
                    name: 'C#',
                    color: '#a27add',
                    years: 2,
                    subData: ['Unity']
                },
                {
                    name: 'Powershell',
                    color: '#002355',
                    alt: '#E8E7DD',
                    years: 2,
                    subData: []
                },
                {
                    name: 'HTML5 & CSS3',
                    color: '#E8E7DD',
                    years: 4,
                    subData: []
                }
            ],
            skills: [
                'Computer Networking',
                'Linux, Windows, & MacOS Administration',
                'Relational Databases',
                'Non-Relational Databases',
                'Docker',
                'Software Reverse Engineering',
                'Pentesting',
                'Fuzzing',
                'Frontend Design',
                'Git'
            ]
        }
    }
}
const art = ` _          _____ _____         
| |__  _   |___  |___  |__ _ __ 
| '_ \\| | | | / /   / / _ \\ '__|
| |_) | |_| |/ /   / /  __/ |   
|_.__/ \\__, /_/   /_/ \\___|_|   
       |___/                    
`
</script>

<style>
#maincont {
    max-width: 800px;
    margin: auto;
    font-size: 19px;
    margin-bottom: 10px;
}

#name {
    font-size: 22px;
}

#age:hover {
    cursor: pointer;
}

#lang_detail {
    margin-top: 10px;
    margin-bottom: 30px;
}

#footer {
    font-size: 15px;
}

@media only screen and (max-width: 600px) {
    #name {
        font-size: 15px;
    }
}

a {
    text-decoration: none;
    font-size: 17px;
    color: #E8E7DD;
}

a:hover {
    cursor: pointer;
    color: #66ff66;
}

.flexc {
    margin: auto;
    max-width: 650px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
}

fieldset {
    margin: auto;
    max-width: 300px;
    border-color: #aaaaaa;
    border-width:1px;
}

.language {
    flex-grow: 1;
}

.text {
    font-family: 'Courier New', Courier, monospace;

}

.red {
    color: #fc4c58;
}

.green {
    color: #66ff66;
}

.dim {
    color: #aaaaaa;
}

.show-enter-active {
  transition: all .3s ease;
}
.show-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.show-enter, .show-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

::selection {
  color: white;
  background: #fc4c58;
}
</style>
