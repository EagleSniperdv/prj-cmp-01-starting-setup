<template>
    <the-header title="Vue complete Hands-on"></the-header>
    <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import StoredResources from './components/learning-resources/StoredResources.vue';
import TheHeader from './components/layouts/TheHeader.vue';

export default{

        components: {
            StoredResources,
            TheHeader,
        },

        data
                () 
            {
                return {
                    storedResources: [
                        {
                            id: "material1",
                            title: "Vue official site",
                            description: "this is the description",
                            link: "www.vue.org"
                        },

                        {
                            id: "material2",
                            title: "Google official site",
                            description: "this is the description for google",
                            link: "www.google.com"
                        },
                    ]
                }
            }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
    box-sizing: border-box;
    }

html {
    font-family: 'Roboto', sans-serif;
}

body {
    margin: 0;
}
    
</style>