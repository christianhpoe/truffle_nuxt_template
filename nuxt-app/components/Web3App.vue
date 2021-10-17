<template>
  <div class="App">
        <h1>Hello World</h1>
  </div>
</template>

<script>
import getWeb3 from "./getWeb3";
/// import Contract from "../../build/contracts/Contract.json"

export default {
    name: "Web3App",
    components: {},
    data() {
        return {
            loading: true,
            accounts: null,
            networkId: null,
            web3: null,
            /// localContract: null,
        }
    },
    computed: {
    },
    watch: {
        
    },
    methods: {
        
        
    },
    
    async mounted() {
      try {
        // Get network provider and web3 instance.
        this.web3 = await getWeb3()
        // Use web3 to get the user's accounts.
        this.accounts = await this.web3.eth.getAccounts()

        // Get the contract instances.
        this.networkId = await this.web3.eth.net.getId()

        /* this.localContract = new this.web3.eth.Contract(
          Contract.abi,
          Contract.networks[this.networkId] && Contract.networks[this.networkId].address,
        ) */
        
        this.loading = false
      } catch (error) {
        // Catch any errors for any of the above operations.
        console.error(
          `Failed to load web3, accounts, or contract. Check console for details.`,
        );
        console.error(error);
      }
    }
}
</script>
