<script>
    import "../app.css";
    import { onMount } from "svelte";
    import { onNavigate } from "$app/navigation";
    import { cursorColor, cursorPosition } from "$lib/stores.js";
    import { passwordEntered } from "$lib/stores.js";

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

            const links = document.querySelectorAll('a');

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

        let password;

        await passwordEntered.subscribe(value => {
            if (!value) {
                document.body.style.filter = 'blur(8px)';
                password = window.prompt("Enter the password to access the site", "");
                if (password === "cwp2024") {
                    passwordEntered.set(true);
                    document.body.style.filter = 'none';
                } else {
                    location.reload();
                }
            }
        });
    });
</script>

<slot />

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
    }
</style>