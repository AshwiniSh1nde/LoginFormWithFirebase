<script>
    import Next from "../lib/cmp/Next.svelte";
    import Login from "../lib/cmp/Login.svelte";
    import { initializeApp } from "firebase/app";
    import { getAuth } from "firebase/auth";

//---------------Write your firebase configuration here --------------
    const firebaseConfig = {
    apiKey: "your-api-key",
    authDomain: "your-project-id.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project-id.appspot.com",
    messagingSenderId: "your-sender-id",
    appId: "your-app-id"
};

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    // Initialize Firebase Authentication and get a reference to the service
    const auth = getAuth(app);
    
    var loggedIn = false; // assume the user is not logged in

    function handleLogin() {
        loggedIn = true;
    }

</script>

{#if !loggedIn}
    <Login {handleLogin} />
{:else}
    <Next />
{/if}
