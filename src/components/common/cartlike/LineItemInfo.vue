<template>
  <div>
    <div class="col-sm-3 col-xs-4 product-img-col">
      <router-link :to="productRoute(lineItem.productSlug, lineItem.variant.sku)"
                   class="img">
        <img :src="displayedImageUrl(lineItem.variant)"
             :alt="lineItem.name"
             class="img-responsive img">
      </router-link>
    </div>
    <div class="col-sm-8 col-xs-offset-1 col-xs-7 product-info-text">
      <p class="cart-item-name product-title">
        <router-link :to="productRoute(lineItem.productSlug, lineItem.variant.sku)"
                     data-test="cart-line-item-link">
          {{ lineItem.name }}
        </router-link>
      </p>
      <p v-if="extended"
         class="grey-p"
         data-test="cart-line-item-sku">
        {{ lineItem.variant.sku }}
      </p>
      <!--<p class="cart-attributes">-->
      <!--{{#each attributes}}-->
      <!--{{name}}-->
      <!--<span class="black-p" data-model="cartItem.{{key}}">{{value}}</span>-->
      <!--{{#unless @last}}<br>{{/unless}}-->
      <!--{{/each}}-->
      <!--</p>-->
      <!--<p class="cart-item-availability grey-p">-->
      <!--<span class="glyphicon glyphicon-ok-sign"></span>{{ $t('catalog:availability.available') }}-->
      <!--</p>-->
    </div>
  </div>
</template>

<script>
import productMixin from '@/mixins/productMixin';

export default {
  props: {
    lineItem: {
      type: Object,
      required: true,
    },
    extended: {
      type: Boolean,
      default: () => true,
    },
  },

  mixins: [productMixin],
};
</script>
