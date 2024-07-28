<script>
    import { fileExcelO } from "svelte-awesome/icons";
    export let project;
    import MediaQuery from "../MediaQuery.svelte";
    import IntersectionObserver from "svelte-intersection-observer";
    import { fade, draw, fly, crossfade, blur } from "svelte/transition";
    /**
     * @type {any}
     */
    let elem1;
    /**
     * @type {any}
     */
    let elem2;
</script>

<IntersectionObserver once element={elem1} let:intersecting>
    <div class="projecte" bind:this={elem1}>
        <slot />
        {#if intersecting}
            <div class="flexbox imgcon" transition:fly={{delay: 200, duration: 1000, x: -1000}}>
                <div class="flexchild">
                    <h1>{project.name}</h1>
                    <p>{project.date}</p>
                    <ul>
                        {#each project.description as bullet}
                            <li>{bullet}</li>
                        {/each}
                    </ul>
                </div>
                <div class="flexchild" style="border-left: none; flex-grow: 2;" transition:fly={{delay: 300, duration: 900, x: -1000}}>
                    <img src={project.image} alt={project.name} />
                </div>
            </div>
        {/if}
    </div>
</IntersectionObserver>

<MediaQuery query="(max-width: 1280px)" let:matches>
    {#if matches}
        <style>
            /* .projecte .flexbox { 
                display: flex !important; 
                flex-direction: column-reverse !important; 
            } */
        </style>
    {/if}
</MediaQuery>

<style>
    .projecte { 
        min-height: 30vh; 
    }
    .flexbox {
        position: relative;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        width: 100%;
    }
    .flexchild {
        position: relative;
        /* height: 50vh; */
        border: 1px solid rgba(255, 255, 255, 0.13);
        border-right: 0;
        top: 0vh;
        flex-grow: 1;
        padding: 0;
        margin: 0;
        border-top: none;
        overflow: hidden;
        flex: 1 1 200px;
    }
    img {
        min-width: 100%;
        min-height: 100%;
        width: auto;
        height: auto;
        padding: 0;
        margin: 0;
        overflow: hidden;
    }
    h1 {
        padding-left: 2vw;
        font-size: 3vw;
        font-weight: normal;
        line-height: 0.8;
        letter-spacing: -0.3vw;
        margin: 3vh 0vw;
    }
    p {
        padding: 1vh 2vw;
    }
    .projecte li { 
        font-size: 3vh; 
        padding: 2vh; 
    }
    .flexchild p { 
        font-size: 3vh; 
    }
</style>
