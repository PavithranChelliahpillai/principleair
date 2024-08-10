<script>
    export let project;

    import IntersectionObserver from "svelte-intersection-observer";
    import { fade, draw, fly, crossfade, blur } from "svelte/transition";
    import MediaQuery from "../MediaQuery.svelte";
    import { cubicInOut } from "svelte/easing";
    import { columns } from "svelte-awesome/icons";
    /**
     * @type {any}
     */
    let elem1;
    /**
     * @type {any}
     */
    let elem2;
</script>

<MediaQuery query="(max-width: 1280px)" let:matches>
    {#if matches}
        <script>
            import { onMount } from "svelte";

            export let timeout = 0;
            export let hidden = false;

            onMount(() => {
                setTimeout(() => {
                    hidden = true;
                }, timeout);
            });
        </script>
        <style>
            .flexbox { 
                flex-direction: column !important;
                height: auto !important;
            }
            .imgcon { 
                height: auto !important;
            }
            .flexchild { 
                max-height: 80vh !important;
            }
        </style>
    {/if}
</MediaQuery>

<IntersectionObserver once element={elem1} let:intersecting>
    <div class="projecte" bind:this={elem1}>
        <slot />
        {#if intersecting}
            <div
                class="flexbox imgcon"
                transition:fly={{
                    delay: 200,
                    duration: 1000,
                    x: 1000,
                    easing: cubicInOut,
                }}
            >
                <div class="flexchild" style="border-left: none; flex-grow: 2;">
                    {#if !project.vid}
                        <img src={project.image} alt={project.name} />
                    {:else}
                        <video
                            src={project.image}
                            muted
                            autoplay
                            loop
                            playsinline
                            disablepictureinpicture
                        />
                    {/if}
                </div>
                <div
                    class="flexchild"
                    transition:fly={{
                        delay: 300,
                        duration: 900,
                        x: 1000,
                        easing: cubicInOut,
                    }}
                >
                    <h1>{project.name}</h1>
                    <ul>
                        {#each project.description as bullet}
                            <li>{bullet}</li>
                        {/each}
                    </ul>
                </div>
                <div class="flexchild" style="border-left: none; flex-grow: 2;">
                    {#if !project.vidt}
                        <img src={project.imaget} alt={project.namet} />
                    {:else}
                        <video
                            src={project.imaget}
                            muted
                            autoplay
                            loop
                            playsinline
                            disablepictureinpicture
                        />
                    {/if}
                </div>
                <div
                    class="flexchild"
                    transition:fly={{
                        delay: 300,
                        duration: 900,
                        x: 1000,
                        easing: cubicInOut,
                    }}
                >
                    <h1>{project.namet}</h1>
                    <ul>
                        {#each project.descriptiont as bullet}
                            <li>{bullet}</li>
                        {/each}
                    </ul>
                </div>
            </div>
        {/if}
    </div>
</IntersectionObserver>

<style>
    .projecte video  { 
        position: relative; 
        left: 50%;
        transform: translateX(-50%); 
        height: 100vh;
    }
    .projecte {
        min-height: 100vh;
        border: 1px solid rgba(255, 255, 255, 0.13);
        border-top: none;
    }
    .imgcon {
        height: 100vh;
    }
    .flexchild h1 {
        margin-right: 2vw;
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
        /* border: 1px solid rgba(255, 255, 255, 0.13); */
        border-right: 0;
        top: 0vh;
        flex-grow: 1;
        padding: 0;
        margin: 0;
        border-top: none;
        overflow: hidden;
        flex: 1 1 200px;
        min-height: 30vh;
    }
    .flexchild > img {
        position: relative;
        width: auto;
        height: auto;
        max-height: 100vh;
    }
    img {
        position: relative; 
        left: 50%;
        transform: translateX(-50%); 
        height: 100vh;
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
