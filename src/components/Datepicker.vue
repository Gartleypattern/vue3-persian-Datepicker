<template>
                <h1>hello iman</h1>
                <input
                         type="text" 
                         class="form-control no-border mx-auto mt-5" 
                         style="width: 320px"
                         v-model= inputDate
                         @click="showDatePicker"
                >
                <div 
                        class="datepicker mx-auto" 
                        v-if='dateShow' 
                >
                        <div class="d-flex justify-content-between mx-3 my-2">
                            <img class="chevron" 
                                        :src="require('../assets/img/chevron-right.png')" 
                                        @click="prevMonth"
                            />
                            <h6> {{months[cMonth] }} {{cYear}}</h6>
                            <img 
                                    class="chevron" 
                                    :src="require('../assets/img/chevron-left.png')" 
                                    @click="nextMonth"
                            />
                        </div>
                        <div  class="daysDiv">
                                <div class="d-flex ">
                                    <div
                                        @click="setDate"
                                        class="days"   
                                        v-for="n in 7" 
                                        :key="n">{{n}}
                                    </div>
                                </div>
                                <div class="d-flex">
                                    <div 
                                        @click="setDate"
                                            class="days1"  
                                            v-for="n in 7" 
                                            :key="n + 7">{{n + 7}}
                                    </div>
                                </div>
                                <div class="d-flex">
                                    <div  
                                        @click="setDate"
                                        class="days2"  
                                        v-for="n in 7" 
                                        :key="n + 14">{{n + 14}}
                                    </div>
                                </div>
                                <div class="d-flex">
                                    <div  
                                        @click="setDate"
                                            class=" days3"  
                                            v-for="n in 7" 
                                            :key="n + 21">{{n + 21}}
                                    </div>
                                </div>
                                <div class="d-flex">
                                    <div  
                                        @click="setDate"
                                        class=" days3"  
                                        v-for="i  in n " 
                                        :key="i +28">{{i + 28}}
                                    </div>
                                </div>
                        </div>
                </div>
</template>

<script>
var moment = require('jalali-moment');

export default {
        name : 'Datepicker',
        data () {
            return{
                inputDate : "",
                dateShow : true,
                months : ['فروردین' , 'اردیبهشت', 'خرداد', 'تیر', 'مرداد', 'شهریور', 'مهر' , 'آبان ', 'آذر', 'دی ', 'دی ', 'بهمن' , 'اسفند'],
                cDay : this.day(),
                cMonth : this.month(),
                cYear : this.year(),
                n: this.populateDate(),
            }
        },
        mounted () {
            this.populateDate();
        },

        methods : {
            showDatePicker () {
                    this.dateShow = !this.dateShow;
            },
            nextMonth () {
                if(this.cMonth ===12){
                    this.cMonth = 0;
                    this.cYear ++;
                }else{
                    this.cMonth ++;
                }
                 this.populateDate();
            },
            prevMonth () {
                if( this.cMonth === 0){
                    this.cMonth=12;
                    this.cYear--;
                }else{
                    this.cMonth --;
                }
                    this.populateDate();
            },
            currentDate () {
                return moment().locale('fa').format('YYYY/M/D');
            },
            day (){
                return moment().locale('fa').format('D');
            },
            month () {
                return moment().locale('fa').format('M') -1 ;
            },
            year () {
                return moment().locale('fa').format('YYYY');
            },
            setDate (event) {
                let slash1 = '/';
                let slash2 = '/';
                if (event.target.textContent <10) {
                    slash2 = '/0'
                }
                if (this.cMonth<10) {
                    slash1 = '/0'
                }
                this.inputDate = this.cYear + slash1 +  (this.cMonth +1) + slash2 + event.target.textContent;
            },
            populateDate () {
                switch(this.cMonth) {
                    case 0: 
                    case 1: 
                    case 2: 
                    case 3: 
                    case 4: 
                    case 5: 
                        this.n = 3;
                        break;
                    case 6: 
                    case 7: 
                    case 8: 
                    case 9: 
                    case 10: 
                    case 11: 
                        this.n = 2;
                        break;
                    case 12: 
                        this.n = 1;
                        break;
                }
                return this.n;
            }
        },
    }
</script>

<style>
    .datepicker {
        width:  320px;
        height:  270px;
        background: white;
        border-top: 1px solid rgb(212, 193, 193);
    }
    .form-control {
        border : none !important;
    }
    .chevron {
        width : 25px;
    }
    .dayItem {
        margin: 2px 5px;
    }
    .dayItem1 {
        margin: 2px 2.5px;
    }
    .dayItem2 {
        margin: 2px 1px;
    }

    .days {
        margin: 15px 18px;
    }
   
    .days:hover, .days1:hover, .days2:hover, .days3:hover {
        cursor: pointer;    
    }

    .days1 {
            margin : 5px 15.5px;
    }
    .days2 {
            margin : 12px 14px;
    }
    .days3 {
            margin : 9px 14px;
    }

    .daysDiv{
        border-top: 1px solid rgb(189, 185, 185);
    }
</style>