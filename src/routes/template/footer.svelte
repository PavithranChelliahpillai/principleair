<script>
    import MediaQuery from "../MediaQuery.svelte";
</script>

<div class="footer">
    <slot />
    <footer>
        <img src="principleairlogo.png" alt="logo" />
        <p style="display: flex; justify-content: center;">info@principleair.com</p>
        <p style="display: flex; justify-content: center;">Copyright © 2024 - All rights reserved</p>
        <p style="display: flex; justify-content: center;">Developed by Pavithran Chelliahpillai</p>
    </footer>
</div>

<MediaQuery query="(max-width: 1280px)" let:matches>
    {#if matches}
        <style>
            .footer p { 
                font-size: 2vh !important;
                padding-bottom: 1vh; 
            }
        </style>
    {/if}
</MediaQuery>


<style>
    .footer { 
        position: static;
        bottom: 0; 
        background-color: rgb(25, 25, 25); 
        padding: 3vh 5vw; 
        z-index: 3; 
    }
    img { 
        width: 3vw; 
        display: flex; 
        flex-grow: 0; 
    }
    footer { 
        display: flex; 
        flex-direction: row; 
        align-items: center; /* Center items vertically */
        flex-wrap: wrap; 
    }
    p { 
        display: flex; 
        flex-grow: 1; 
        text-align: center; /* Center text horizontally within each <p> */
        padding: 0 3vw; 
        margin: auto; 
        font-size: inherit; 
    }
</style>
