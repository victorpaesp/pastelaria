<template>
  <div class="testando">
      <input
        placeholder="John Doe"
        v-model="name"
        @blur="createEmployee(name, date)"
      />
      <button round slot="reference" type="success"
        >Add New Employee</button      >
    
        
  </div>
</template>

<script>
        import firebase from "../../firebaseInit";
        const db = firebase.firestore();
        export default {
            name: 'Testando',
        data() {
            return {
            name: "",
            date: new Date().toISOString().slice(0, 10),
            employeesData: [],
            search: "",
            };
        },
        methods: {
            createEmployee(name, date) {
            if (name != "") {
                db.collection("employees")
                .add({ date: date, name: name })
                .then(() => {
                    console.log("Document successfully written!");
                    this.readEmployees();
                })
                .catch((error) => {
                    console.error("Error writing document: ", error);
                });
                this.name = "";
            }
            },
            readEmployees() {
            this.employeesData = [];
            db.collection("employees")
                .get()
                .then((querySnapshot) => {
                querySnapshot.forEach((doc) => {
                    this.employeesData.push({
                    id: doc.id,
                    name: doc.data().name,
                    date: doc.data().date,
                    });
                    console.log(doc.id, " => ", doc.data());
                });
                })
                .catch((error) => {
                console.log("Error getting documents: ", error);
                });
            },
            updateEmployee(id, name, date) {
            db.collection("employees")
                .doc(id)
                .update({
                name: name,
                date: date,
                })
                .then(() => {
                console.log("Document successfully updated!");
                this.readEmployees();
                })
                .catch((error) => {
                // The document probably doesn't exist.
                console.error("Error updating document: ", error);
                });
            },
            deleteEmployee(id) {
            db.collection("employees")
                .doc(id)
                .delete()
                .then(() => {
                console.log("Document successfully deleted!");
                this.readEmployees();
                })
                .catch((error) => {
                console.error("Error removing document: ", error);
                });
            },
        },
        mounted() {
            this.readEmployees();
        },
        };
</script>


<style>
    .testando {
      z-index: 10;
      background-color: red;
      width: 500px;
      height: 500px;
    }
</style>