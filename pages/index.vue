<template>
  <div>
    <router-link to="/collections">Collection</router-link>
    <h1 class="text-3xl">Saluto</h1>
    <p>
      <button @click="readContacts">Read Contacts</button>
      <br>
      <br>
      <button @click="addContact">save new Contacts</button>
    </p>

    <pre id="log"></pre>
  </div>
</template>

<script>
export default {
  layout: "blog",
  methods: {
    readContacts() {
      var api = (navigator.contacts || navigator.mozContacts);

      if (api && !!api.select) { // new Chrome API
        api.select(['name', 'email'], { multiple: true })
          .then(function (contacts) {
            consoleLog('Found ' + contacts.length + ' contacts.');
            if (contacts.length) {
              consoleLog('First contact: ' + contacts[0].name + ' (' + contacts[0].email + ')');
              consoleLog('First contact: ' + contacts[0]);
            }
          })
          .catch(function (err) {
            consoleLog('Fetching contacts failed: ' + err.name);
          });

      } else if (api && !!api.find) { // old Firefox OS API
        var criteria = {
          sortBy: 'familyName',
          sortOrder: 'ascending'
        };

        api.find(criteria)
          .then(function (contacts) {
            consoleLog('Found ' + contacts.length + ' contacts.');
            if (contacts.length) {
              consoleLog('First contact: ' + contacts[0].givenName[0] + ' ' + contacts[0].familyName[0]);
            }
          })
          .catch(function (err) {
            consoleLog('Fetching contacts failed: ' + err.name);
          });

      } else {
        consoleLog('Contacts API not supported.');
      }
    },

    saveNewContact() {
      // create a new contact object
      alert("Contact entrain de sauvegarder")
      var api = (navigator.contacts || navigator.mozContacts);
      var contact = api.create();
      contact.displayName = "Plumber";
      contact.nickname = "Plumber";            // specify both to support all devices

      // populate some fields
      var name = new ContactName();
      name.givenName = "Jane";
      name.familyName = "Doe";
      contact.name = name;

      // save to device
      contact.save(onSuccess, onError);

      this.consoleLog(contact)

      alert("Contact sauvegarder")

    },

    consoleLog(data) {
      var logElement = document.getElementById('log');
      logElement.innerHTML += data + '\n';
    },

    onSuccess(contact) {
      alert("Save Success");
    },

    onError(contactError) {
      alert("Error = " + contactError.code);
    },

    addContact() {
      var displayName = "Jane";
      var name = "DOe Doe";
      var phoneNumber = "+22899999999";
      try {
        var results = document.getElementById('contact_results');
        var contact = navigator.contacts.create({ "displayName": displayName, "name": name, "note": "DeleteMe" });

        var phoneNumbers = [1];
        phoneNumbers[0] = new ContactField('work', phoneNumber, true);
        contact.phoneNumbers = phoneNumbers;

        contact.save(function () {
          results.innerHTML = (displayName || "Nameless contact") + " saved.";
        }, function (e) {
          alert("contact saved")
          if (e.code === ContactError.NOT_SUPPORTED_ERROR) {
            results.innerHTML = "Saving contacts not supported.";
          } else {
            results.innerHTML = "Contact save failed: error " + e.code;
          }
        });
      } catch (e) {
        console.error(e.message);
      }
    }

  }
}
</script>