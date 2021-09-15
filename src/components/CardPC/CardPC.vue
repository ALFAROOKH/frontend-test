<template>
    <div class="card" >
        {{pc}}
        <img :src="pc.logo_path">
    </div>
</template>

<script>
export default {
    name: "CardPC",
    props: ["pc"]
}
</script>
