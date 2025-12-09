<template>
    <li>
        
        {{ tasks }}
        <button style="background-color:  green;" @click="">edit</button>
        <button style="background-color:  red;" @click="$emit('remove')">delete</button>
    </li>
</template>

<script>
export default{
    name: "TodoItem",
    props:{
        tasks:{
            type: String,
            required: true,
        },
    },
};
</script>

<style>
li{
    list-style: none;
    margin: 10px 0;
}
button{
    margin-left: 10px;
}

</style>