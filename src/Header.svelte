<script>
    export let title;
    export let socials;
    export let img;
</script>
<style>    
   

    /* zocial */
    [class*="zocial-"]:before {
        font-family: 'zocial', sans-serif;
    }

    h1{
        font-family: 'Barriecito';
        width:60vw;
        float: left;
        color: #555;
    }
    img.banner{
        margin:0 auto;
        width:100vw;
        height: 500px;
        object-fit: cover;
    }
    .socialbar{float:right;width:30vw;}
    .socialbar a{
        border-radius: 15%;
        border: 1px solid #EEE;
        background: #FFF;
        color: #555;
        width:75px;
        height: 25px;
        padding-top:12.5px;
        padding-bottom:12.5px;
        margin-left:10px;
        float:right;
        vertical-align: middle;
        text-align: center;
    }
    .socialbar a:hover{
        color: #FFF;
        background-color:#555;
        text-decoration:none;
    }
</style>
<header>
    <h1>{title}</h1>
      <span class="socialbar">
        {#each socials as {zocialIcon, url}, idx}
            {#if url!==''}
                <a href="{url}" ><span class="zocial-{zocialIcon}"></span></a>
            {/if}
        {/each}
    </span>
    <img class="banner" src="{img.url}" alt="{img.desc}">
  
</header>