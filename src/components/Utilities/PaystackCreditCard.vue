<template>
<div>
    <v-card v-bind="$attrs" v-if="card" outlined>
    <v-card-title >
        <h4> **** **** **** {{ card.last4 }}</h4>
        <v-spacer></v-spacer>
        {{ card.card_type }}
        <!-- <v-img src="@/assets/img/credit-cards/visa.png" width="20"></v-img> -->
    </v-card-title>
    <v-card-text class="d-flex">
      <div>
        <p>{{ card.bank }} <span class="ml-2">Expires {{ card.exp_month }}/{{ card.exp_year }}</span></p>
        <p>via Paystack</p>
      </div>
      <v-spacer></v-spacer>
      <slot name="actions" v-bind="{ card }" />
    </v-card-text>
</v-card>
<v-card v-else v-bind="$attrs" outlined>
    <v-card-text>
        <p class="grey--text text-center my-3">No credit card</p>
    </v-card-text>
</v-card>

</div>
</template>

<script>
export default {
    name: "PaystackCreditCard",
    data(){
        return {
            cards: {
                visa: 'visa.png',
                mastercard: 'mastercard.png'
            }
        }
    },
    props: {
        card: Object
    },

}
</script>