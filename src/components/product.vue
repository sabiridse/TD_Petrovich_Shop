<template>
    <div id="products_section">
        <div class="products_page pg_0">
            <div class="product product_horizontal">                                
                <span class="product_code">Код: {{prod.code}}</span>
                <div class="product_status_tooltip_container">
                    <span class="product_status">Наличие</span>
                </div>                                
                <div class="product_photo">
                    <a href="#" class="url--link product__link">
                        <!-- <img src="misc/df126-52f2-11e5-b9a9-00259036a192_220x220_1.jpg"> -->
                        <img :src="prod.primaryImageUrl">
                    </a>                                    
                </div>
                <div class="product_description">
                    <a href="#" class="product__link">{{prod.title}}</a>
                </div>
                <div class="product_tags hidden-sm">
                    <p>Могут понадобиться:</p>
                    <a href="#" class="url--link">{{prod.assocProducts}}</a>
                    <!-- <a href="#" class="url--link">плинтус натуральный,</a>
                    <a href="#" class="url--link">рулетка,</a>
                    <a href="#" class="url--link">набор для укладки ламината,</a>
                    <a href="#" class="url--link">ножовка по ламинату,</a>
                    <a href="#" class="url--link">гель для стыков ламината Clic Protect.</a> -->
                </div>
                <div class="product_units">
                    <div class="unit--wrapper">
                        <div :class="unitSelect1">
                            <p class="ng-binding" @click="unitSelectChoise1">За м. кв.</p>
                        </div>
                        <div :class="unitSelect2">
                            <p class="ng-binding" @click="unitSelectChoise2">За упаковку</p>
                        </div>
                    </div>
                </div>
                <p class="product_price_club_card">
                    <span class="product_price_club_card_text">По карте<br>клуба</span>
                    <span class="goldPrice">{{priceGold}}</span>
                    <span class="rouble__i black__i">
                        <svg version="1.0" id="rouble__b" xmlns="http://www.w3.org/2000/svg" x="0" y="0" width="30px" height="22px" viewBox="0 0 50 50" enable-background="new 0 0 50 50" xml:space="preserve">
                           <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#rouble_black"></use>
                        </svg>
                     </span>
                </p>
                <p class="product_price_default">
                    <span class="retailPrice">{{priceRetail}}</span>
                    <span class="rouble__i black__i">
                        <svg version="1.0" id="rouble__g" xmlns="http://www.w3.org/2000/svg" x="0" y="0" width="30px" height="22px" viewBox="0 0 50 50" enable-background="new 0 0 50 50" xml:space="preserve">
                           <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#rouble_gray"></use>
                        </svg>
                     </span>
                </p>
                <div class="product_price_points">
                    <p class="ng-binding">Можно купить за 231,75 балла</p>
                </div>
                <div class="list--unit-padd"></div>
                <div class="list--unit-desc">
                    <div class="unit--info">
                        <div class="unit--desc-i"></div>
                        <div class="unit--desc-t">
                            <p>
                                <span class="ng-binding">Продается упаковками:</span>
                                <span class="unit--infoInn">1 упак. = 2.47 м. кв. </span>
                            </p>
                        </div>
                    </div>
                </div>
                <div class="product__wrapper">
                    <div class="product_count_wrapper">
                        <div class="stepper">
                            <input class="product__count stepper-input" type="text" :value="count">
                            <span class="stepper-arrow up" @click="countUp"></span>
                            <span class="stepper-arrow down" @click="countDown"></span>                                           
                        </div>
                    </div>
                    <span class="btn btn_cart" data-url="/cart/" data-product-id="9bf0afd7-5190-11e5-b9a9-00259036a192">
                        <svg class="ic ic_cart">
                           <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#cart"></use>
                        </svg>
                        <span class="ng-binding">В корзину</span>
                    </span>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
	export default {
		data(){
			return{
				code:0,
				nameprod:"non",
				count:1,
				unitSelect2:"unit--select unit--active",
				unitSelect1:"unit--select",
				priceGold: this.prod.priceGold,
				priceRetail: this.prod.priceRetail
			}
		},
		name: 'product',
		props: ['prod'],
		methods: {
			countUp(){
				this.count++;
			},
			countDown(){
				if(this.count>0){
					this.count--;
				}				
			},
			unitSelectChoise1(){
				if(this.unitSelect1 == "unit--select unit--active"){
					this.unitSelect1="unit--select";
					this.unitSelect2="unit--select unit--active";
					this.priceGold=this.prod.priceGoldAlt;
					this.priceRetail=this.prod.priceRetailAlt;
				};
				if(this.unitSelect1 == "unit--select"){
					this.unitSelect2="unit--select";
					this.unitSelect1="unit--select unit--active";
					this.priceGold=this.prod.priceGold;
					this.priceRetail=this.prod.priceRetail;
				};
			},
			unitSelectChoise2(){
				if(this.unitSelect2 == "unit--select unit--active"){
					this.unitSelect2="unit--select";
					this.unitSelect1="unit--select unit--active";
					this.priceGold=this.prod.priceGold;
					this.priceRetail=this.prod.priceRetail;
				};
				if(this.unitSelect2 == "unit--select"){
					this.unitSelect1="unit--select";
					this.unitSelect2="unit--select unit--active";
					this.priceGold=this.prod.priceGoldAlt;
					this.priceRetail=this.prod.priceRetailAlt;
				};
			}
		}
	};
</script>
<style>
</style>