<template>
  <div class="Valipank">
    <img alt="Vue logo" src="../assets/logovp.jpg">
    <h1 id="h1">Internetipank</h1>

    <h3 id="hakka_kliendiks"> Hakka kliendiks</h3>
    <p>Sisesta enda andmed tabelisse ja vajuta "Tulen üle" nupule.</p>

    <table name="newClientTable" border="1" align="center" >
      <tr>
        <th>Eesnimi</th>
        <th>Perekonnanimi</th>
        <th>Isikukood</th>
      </tr>
      <tr>
        <td><input id="fName" type="text"></td>
        <td><input id="lName" type="text"></td>
        <td><input id="iDCode" type="number"></td>
      </tr>
    </table>

    <a href="https://github.com/siimrebane/vali-it">Tutvu tingimustega</a>
    <p><input id="createClientButton" type="button" value="Tulen üle"></p>

    <h3 id="createAccountHeader"> Loo konto</h3>
    <p>Uue konto loomiseks sisesta enda kliendi nr <input id="clientNoForNewAccount" type="number">
      ja vajuta <input id="createAccountButton" type="button" value="sellele nupule."></p>

    <h3 id="clientAccountsHeader"> Kliendi kontod</h3>
    <p>Vaata klient nr <input id="clientNoForAccounts" type="number" > <input id="myAccountsButton" type="button" value="kontosid."></p>
    <div id="myAccountsContent">
    </div>
    <br>

    <h3 id="konoto_seis"> Konto seis</h3>
    <p>Vaata konto nr <input id="clientNoForBalance" type="number" > <input id="balanceButton" type="button" value="seisu."></p>
    <div id="myBalanceContent">
    </div>
    <br>

    <h3 id="historyHeading"> Tehingute ajalugu</h3>
    <p>Vaata konto nr <input id="clientNoForHistory" type="number" > tehingute ajalugu <input id="historyButton" type="button" value="siit."></p>
    <div id="historyContent">
    </div>
    <br>

    <h3 id="allAccountsHeader"> Kõik kontod</h3>
    <p>Kõigi kontode nimekirja saab <button v-on:click="getAccountsList()">Siit</button></p>
    <div id="accountsContent">
    </div>
    <table>
      <tr>
        <th> Account no</th>
        <th> Client no</th>
        <th> Balance </th>
      </tr>
      <tr v-for="row in accountsList">
        <td> {{accountNo }}</td>
        <td> {{clientNo}}</td>
        <td> {{balance}}</td>
      </tr>
    </table>
    <br>
  </div>
</template>

<script>
let fAccountsList = function (accounts){
  let url = "http://localhost:8080/accounts";
  this.accountsList = accounts.data;
}

export default {
  name: 'Valipank',
  methods: {
    getAccountsList: fAccountsList()
  },
  data: function () {
    return {
      // email: "",
      //user: {},
      accountsList: [],
      accountNo : this.accountNo,
      clientNo : this.clientNo,
      balance : this.balance
    }
  }
}

</script>
