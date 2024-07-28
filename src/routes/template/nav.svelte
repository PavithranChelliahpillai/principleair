<script>
    /**
     * @type {any}
     */
    let y;
    import MediaQuery from "../MediaQuery.svelte";
</script>

{#if y > 0}
    <style>
        #home, #about, #contact, #projects {
            background-color: rgba(0, 0, 0, 0.9); 
        }
        #home:hover, #about:hover, #contact:hover, #projects:hover {
            background-color: rgba(255, 255, 255, 0.2); 
        }
    </style>
{/if}

<div class="navbar">
    <slot />
    <ul>
        <li id="home" style="padding: 0;"><a href="/">Home</li>
        <li id="about"><a href="/about">About Us</li>
        <li id="projects"><a href="/projects">Our Projects</li>
        <li id="contact"><a href="/contact">Contact Us</li>
    </ul>
</div>

<style>
    .navbar { 
        display: relative; 
        height: 7vh; 
        z-index: 500; 
    }
    ul {
        display: flex; flex-direction: row; 
        margin: 0; padding: 0; 
        list-style-type: none;
        position: fixed; width: 100%; 
    }
    li {
        float: left;
        border: 1px solid rgba(255, 255, 255, 0.39); 
        border-right: 0; 
        position: relative;
        flex: 1 1 0px;
        transition: all 0.5s; 
    }
    a {
        text-decoration: none; 
        color: white; 
        height: 2vh; padding-left: 1vw; 
        display: block; 
        padding-top: 2.5vh; padding-bottom: 2.5vh; 
    }
    li:hover { 
        background: rgba(17, 17, 17, 0.9); 
    }
    #home { 
        flex-grow: 2; 
        border-left: 0; 
    }
    #contact { 
        flex-grow: 2; 
    }
</style>

<svelte:window bind:scrollY={y} />

<MediaQuery query="(max-width: 480px)" let:matches>
    {#if matches}
        <style>
            .navbar {
                display: none;
            }
            .dispapp p {
                font-size: 2vw !important;
            }
            .dispapp h1 {
                font-size: 3vw !important;
            }
        </style>
    {/if}
</MediaQuery>