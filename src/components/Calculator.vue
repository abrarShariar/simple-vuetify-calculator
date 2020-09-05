<template>
  <v-app id="inspire">
    <v-main>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="4"
          >
            <v-card class="elevation-12">
              <v-toolbar
                color="primary"
                dark
                flat
              >
                <v-toolbar-title>Calculator</v-toolbar-title>
                <v-spacer></v-spacer>                
              </v-toolbar>
              <v-card-text>
                <v-container class="grey lighten-5">
                    <v-row no-gutters>
                        <v-col
                            v-for="n in keys"
                            :key="n"
                            cols="12"
                            md="3"
                        >
                            <v-card
                                class="pa-2"
                                outlined
                                tile
                                >
                                <v-btn :value="n" class="mx-2" fab dark small color="primary" @click="setKey(n)" v-if="n != 'R'">
                                    <span>
                                        {{ n }}
                                    </span> 
                                </v-btn>

                                <v-btn v-if="n == 'R'" class="mx-2" fab small @click="setKey(n)">
                                  <span>
                                     <i class="fas fa-redo"></i>
                                  </span>
                                </v-btn>
                            </v-card>
                        </v-col>
                    </v-row>
                    <v-spacer></v-spacer>
                    <v-row no-gutters>
                        <v-textfield>
                            <i class="fas fa-sync-alt"></i>
                            Input: {{ input }}
                        </v-textfield>
                        <v-spacer></v-spacer>
                        <v-textfield>
                            Output: {{ output }}
                        </v-textfield>
                    </v-row>
                </v-container>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'Calculator',
    data () {
        return {
            input: '',
            output: 0,
            keys: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '+', '-', '*', '/', '=', 'R']
        }
    },
    methods: {
        setKey(key) {
            if (key === '=') {
                this.calculate()
                return
            }
            else if (key === 'R') {
                this.input = []
                this.output = 0
                return
            }
            this.input += key
        },
        calculate () {
          this.output = eval(this.input)
        }
    }
  }
</script>