<template>
  <v-row justify="center">
    <v-dialog
      transition="dialog-bottom-transition"
      v-model="dialog"
      persistent
      :max-width="maxWidth"
    >
      <v-card>
        <v-card-title class="headline lighten-3">
          Confirm
        </v-card-title>
        <v-card-text>
            <slot />
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="red darken-1"
            text
            @click="close"
          >
            Cancel
          </v-btn>
          <v-btn
            color="green darken-1"
            text
            @click="confirm"
          >
            Confirm
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
  export default {
    name: "ConfirmationDialog",
    data () {
      return {
        dialog: false,
      }
    },
    props: {
      maxWidth: {
        default: 300
      }
    },
    methods:{
        open(){
            this.dialog = true;
        },

        close(){
            this.dialog = false;
        },

        confirm(){
            this.$emit('confirmed');
            this.close();
        }
    }
  }
</script>