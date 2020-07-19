<template>
  <div class="cards">
      <div class="row">
        <div class="col-lg-3 col-sm-6">
            <div class="card-box bg-blue">
                <div class="inner">
                    <h3> {{ dolar }}  </h3>
                    <p> Dólar </p>
                </div>
                <div class="icon">
                    <i class="fa fa-dollar-sign" aria-hidden="true"></i>
                </div>
            </div>
        </div>

        <div class="col-lg-3 col-sm-6">
            <div class="card-box bg-green">
                <div class="inner">
                    <h3> {{ euro }} </h3>
                    <p> Euro </p>
                </div>
                <div class="icon">
                    <i class="fa fa-euro-sign" aria-hidden="true"></i>
                </div>
            </div>
        </div>
        <div class="col-lg-3 col-sm-6">
            <div class="card-box bg-orange">
                <div class="inner">
                    <h3> {{ bitcoin }} </h3>
                    <p> Bitcoin </p>
                </div>
                <div class="icon">
                    <i class="fab fa-bitcoin" aria-hidden="true"></i>
                </div>
            </div>
        </div>
        <div class="col-lg-3 col-sm-6">
            <div class="card-box bg-red">
                <div class="inner">
                    <h3> {{ eth }} </h3>
                    <p> Ethereum </p>
                </div>
                <div class="icon">
                    <i class="fab fa-ethereum"></i>
                </div>                
            </div>
        </div>
    </div>
    <div class="row">
        <div class="col-lg-3 col-sm-6">
            
        </div>
    </div>

  </div>
</template>

<script>

export default {
  name: "Cards",
  data(){
      return{
          dolar: 0,
          euro: 0,
          bitcoin: 0,
          eth: 0
      }
  },
  created() {
    return fetch('https://api.coingecko.com/api/v3/exchange_rates')
    .then(res => res.json())
    .then(res => {
        this.dolar = (res.rates.brl.value / res.rates.usd.value).toFixed(2).replace('.', ','), 
        this.euro = (res.rates.brl.value / res.rates.eur.value).toFixed(2).replace('.', ','),
        this.bitcoin = (res.rates.brl.value / res.rates.btc.value).toFixed(2).replace('.', ','),        
        this.eth = (res.rates.brl.value / res.rates.eth.value).toFixed(2).replace('.', ',')
    });    
  }

};

</script>

<style scoped>

.card-box {
    position: relative;
    color: #fff;
    padding: 20px 10px 40px;
    margin: 20px 0px;
}
.card-box:hover {
    text-decoration: none;
    color: #f1f1f1;
}
.card-box:hover .icon i {
    font-size: 100px;
    transition: 1s;
    -webkit-transition: 1s;
}
.card-box .inner {
    padding: 5px 10px 0 10px;
}
.card-box h3 {
    font-size: 27px;
    font-weight: bold;
    margin: 0 0 8px 0;
    white-space: nowrap;
    padding: 0;
    text-align: left;
}
.card-box p {
    font-size: 15px;
}
.card-box .icon {
    position: absolute;
    top: auto;
    bottom: 5px;
    right: 5px;
    z-index: 0;
    font-size: 72px;
    color: rgba(0, 0, 0, 0.15);
}
.card-box .card-box-footer {
    position: absolute;
    left: 0px;
    bottom: 0px;
    text-align: center;
    padding: 3px 0;
    color: rgba(255, 255, 255, 0.8);
    background: rgba(0, 0, 0, 0.1);
    width: 100%;
    text-decoration: none;
}
.card-box:hover .card-box-footer {
    background: rgba(0, 0, 0, 0.3);
}
.bg-blue {
    background-color: #00c0ef !important;
}
.bg-green {
    background-color: #00a65a !important;
}
.bg-orange {
    background-color: #f39c12 !important;
}
.bg-red {
    background-color: #d9534f !important;
}


</style>
