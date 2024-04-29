<script>
    import "../app.css";
    import { onMount } from "svelte";
    import { onNavigate } from "$app/navigation";
    import { cursorColor, cursorPosition } from "$lib/stores.js";
    import { passwordEntered } from "$lib/stores.js";

    let passwordInput = "";
    let isDesktop = true;

    const checkPassword = () => {
        if (passwordInput === "cwp2024") {
            passwordEntered.set(true);
        } else {
            passwordInput = "";
            alert("Incorrect password");
        }
    }

    onNavigate((navigation) => {
        if (!document.startViewTransition) return;

        return new Promise((resolve) => {
            document.startViewTransition( async() => {
                resolve();
                await navigation.complete;
            });
        });
    })

    let circleElement;
    let mouse = { x: 0, y: 0 };
    let circle = { x: 0, y: 0 };
    let previousMouse = { x: 0, y: 0 };
    let currentScale = 0;
    let currentAngle = 0;
    const speed = 0.35;

    onMount(async () => {
        const checkWindowSize = () => {
            isDesktop = window.innerWidth > 1023;
        };

        window.addEventListener('resize', checkWindowSize);
        checkWindowSize();

        let currentCursorColor;

        cursorPosition.subscribe(value => {
            circle.x = value.x;
            circle.y = value.y;
        });

        window.addEventListener('mousemove', (e) => {
            mouse.x = e.x;
            mouse.y = e.y;
            cursorPosition.set({ x: e.x, y: e.y });
        });

        const tick = () => {
            const oldCircleX = circle.x;
            const oldCircleY = circle.y;

            circle.x += (mouse.x - circle.x) * speed;
            circle.y += (mouse.y - circle.y) * speed;

            const deltaCircleX = circle.x - oldCircleX;
            const deltaCircleY = circle.y - oldCircleY;

            const circleVelocity = Math.min(Math.sqrt(deltaCircleX**2 + deltaCircleY**2) * 4, 150);
            const scaleValue = (circleVelocity / 150) * 0.5;
            currentScale += (scaleValue - currentScale) * speed;

            const angle = Math.atan2(deltaCircleY, deltaCircleX);
            if (circleVelocity > 20) {
                currentAngle = angle;
            }

            const links = document.querySelectorAll('a, button');

            // Add mouseover and mouseout event listeners to all links
            links.forEach(link => {
                link.addEventListener('mouseover', () => {
                    cursorColor.subscribe(value => {
                        currentCursorColor = value;
                        circleElement.style.border = `9px dotted ${currentCursorColor}`;
                    });
                    circleElement.style.width = '30px';
                    circleElement.style.height = '30px';
                });
                link.addEventListener('mouseout', () => {
                    cursorColor.subscribe(value => {
                        currentCursorColor = value;
                        circleElement.style.border = `6px solid ${currentCursorColor}`;
                    });
                    circleElement.style.width = '12px';
                    circleElement.style.height = '12px';
                });
                link.addEventListener('click', () => {
                    cursorColor.subscribe(value => {
                        currentCursorColor = value;
                        circleElement.style.border = `6px solid ${currentCursorColor}`;
                    });
                    circleElement.style.width = '12px';
                    circleElement.style.height = '12px';
                });
            });

            circleElement.style.transform = `translate(${circle.x}px, ${circle.y}px) rotate(${currentAngle}rad) scale(${1 + currentScale}, ${1 - currentScale})`;

            window.requestAnimationFrame(tick);

        }
        tick();
    });
</script>

{#if !isDesktop}
    <div class="w-screen h-screen bg-white flex items-center justify-center absolute z-[10000] cursor-none">
        <p class="text-2xl text-center">Sorry, this site can only be viewed in desktop mode (horizontal view).</p>
    </div>
{/if}

{#if !$passwordEntered}
    <div class="w-screen h-screen bg-white flex flex-col items-center justify-center absolute z-[9999] cursor-none">
        <div class="flex flex-col items-center">
            <p class="text-4xl font-bold">Creative Writing Poetry</p>
            <p class="text-2xl">- Portfolio 2024 -</p>
            <p class="text-3xl">Z0177908</p>
        </div>
        <span class="h-96 inline-block" />
        <form on:submit|preventDefault={checkPassword} class="flex flex-col items-center">
            <input type="password" placeholder="enter password" bind:value={passwordInput}
            class="border-2 border-dashed w-full mb-10 cursor-none rounded-lg text-center"
            />
            <span class="h-2 inline-block" />
            <button type="submit" class="bg-black text-white rounded-2xl w-[2.5rem] cursor-none hover:bg-[#41fd16] transition-all flex items-center justify-center">
                <svg
                        width="24"
                        height="24"
                        viewBox="0 0 24 24"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                            d="M15.4857 20H19.4857C20.5903 20 21.4857 19.1046 21.4857 18V6C21.4857 4.89543 20.5903 4 19.4857 4H15.4857V6H19.4857V18H15.4857V20Z"
                            fill="currentColor"
                    />
                    <path
                            d="M10.1582 17.385L8.73801 15.9768L12.6572 12.0242L3.51428 12.0242C2.96199 12.0242 2.51428 11.5765 2.51428 11.0242C2.51429 10.4719 2.962 10.0242 3.51429 10.0242L12.6765 10.0242L8.69599 6.0774L10.1042 4.6572L16.4951 10.9941L10.1582 17.385Z"
                            fill="currentColor"
                    />
                </svg>
            </button>
        </form>
    </div>
{/if}

<div class="slot relative">
<slot />
</div>

<div class="circle" bind:this={circleElement} />

<style>

    :global(:root) {
        cursor: none;
    }

    :global(a){
        cursor: none;
    }

    * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
    }

    .circle {
        --circle-size: 14px;
        position: fixed;
        height: var(--circle-size);
        width: var(--circle-size);
        border: 7px solid black;
        border-radius: 100%;
        top: calc(var(--circle-size) / 2 * -1);
        left: calc(var(--circle-size) / 2 * -1);
        pointer-events: none;
        transition: border 0.3s ease, width 0.3s ease, height 0.3s ease;
        z-index: 9999;
    }
</style>