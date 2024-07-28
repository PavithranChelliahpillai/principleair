<script>
    import Navbar from "../template/nav.svelte";
    import Navphone from "../template/navphone.svelte";
    import Footer from "../template/footer.svelte";
    import Projecte from "./projecteven.svelte";
    import Projecto from "./projectodd.svelte";

    let projects = [
        {
            name: "Project 1",
            image: "/proj1.jpg",
            date: "11/11/1111",
            description: [
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
            ],
        },
        {
            name: "Project 2",
            image: "/proj2.jpg",
            date: "11/11/1111",
            description: [
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
            ],
        },
        {
            name: "Project 3",
            image: "/proj3.jpg",
            date: "11/11/1111",
            description: [
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
            ],
        },
        {
            name: "Project 4",
            image: "/proj4.jpg",
            date: "11/11/1111",
            description: [
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
                "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dignissimos, id.",
            ],
        },
    ];
    let cnt = 0;
    let good = true;
    import MediaQuery from "../MediaQuery.svelte";

    import IntersectionObserver from "svelte-intersection-observer";
    import { fade, draw, fly, crossfade, blur } from "svelte/transition";
    import { cubicInOut } from "svelte/easing";
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
        <style>
            h1 {
                font-size: 5vh !important;
            }
            p {
                font-size: 3vh !important;
                padding-bottom: 1vh;
            }
            #phone {
                display: flex !important;
            }
            #phonebye {
                display: none !important;
            }
            #phone h1 {
                font-size: 3vh !important;
            }
            body {
                overflow-x: hidden !important;
            }
            .flexbox {
                display: block !important;
            }
            #bgp {
                padding-top: 12vh !important;
            }
            img {
                object-fit: cover !important;
            }
        </style>
    {/if}
</MediaQuery>

<body>
    <div id="phonebye" style="position: fixed; z-index: 5;">
        <Navbar></Navbar>
    </div>
    <div id="phone" style="position: fixed; z-index: 5;">
        <Navphone></Navphone>
    </div>
    <IntersectionObserver once element={elem1} let:intersecting>
        <div
            class="flexbox"
            id="bgp"
            style="padding-top: 7vh;"
            bind:this={elem1}
        >
            {#if intersecting}
                <div
                    class="flexchild"
                    style="border-left: 0; min-height: 22vh;"
                >
                    <h1
                        style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin: 3vh 0vw;"
                        transition:fade={{ delay: 200, duration: 750, easing: cubicInOut}}
                    >
                        Our Projects
                    </h1>
                    <p
                        style="width: 50%;"
                        transition:fade={{ delay: 400, duration: 350 }}
                    >
                        Explore the wide variety of projects in our catalogue.
                        The catalogue showcases all our services, including
                        residential, commercial, and industrial applications.
                    </p>
                </div>
            {/if}
            <div class="flexchild" style="width: 100%; flex-grow: 2;"></div>
        </div>
    </IntersectionObserver>
    <MediaQuery query="(max-width: 1280px)" let:matches>
        {#each projects as project, idx}
            {#if idx % 2 == 0 && !matches}
                <Projecte {project} />
            {:else}
                <Projecto {project} />
            {/if}
        {/each}
    </MediaQuery>
    <Footer></Footer>
</body>

<style>
    body {
        overflow-x: hidden;
    }
    .flexbox {
        position: relative;
        display: flex;
        flex-direction: row;
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
        padding-left: 2vw;
    }
    #phone {
        display: none;
    }
</style>
