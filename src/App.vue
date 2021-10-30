<template>
    <div>
            <datepicker />
    </div>
</template>

<script>
import Datepicker from './components/Datepicker.vue';
export default {
  name: 'App',
  components: {
    Datepicker
  }
}
</script>

<style>
input, h6,span {
	font-family: 'IRANSansXFaNum' !important;
	text-align: center;
}


    @font-face {
	font-family: 'IRANSansX';
	font-style: normal;
	font-weight: 700;
	src:local('IRANSansX'),
   url('./fonts/IRANSansX-Bold.woff') format('woff'),   
	local('IRANSansX'),url('./fonts/IRANSansX-Bold.woff2') format('woff2');	 
}

@font-face {
	font-family: 'IRANSansXFaNum';
	font-style: normal;
	font-weight: 700;
	src: local('IRANSansXFaNum'), url('./fonts/IRANSansXFaNum-Bold.woff2') format('woff2');	
}

@font-face {
	font-family: 'IRANSansX';
	font-style: normal;
	font-weight: 400;
	src: local('IRANSansX'), url('./fonts/IRANSansX-Regular.woff') format('woff'),   
	local('IRANSansX'), url('./fonts/IRANSansX-Regular.woff2') format('woff2');	
}

@font-face {
	font-family: 'IRANSansXFaNum';
	font-style: normal;
	font-weight: 400;
	src: local('IRANSansXFaNum'), url('./fonts/IRANSansXFaNum-Regular.woff') format('woff');	
}

 
</style>
