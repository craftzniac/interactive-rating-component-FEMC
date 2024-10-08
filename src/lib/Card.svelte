<script lang="ts">
    import IconStar from "$lib/images/icon-star.svg";
    import ThankYouIllustration from "$lib/images/illustration-thank-you.svg";
    let levels = [1, 2, 3, 4, 5];
    let selectedLevel = -1;
    let reviewSubmitted = false;
</script>

<div class="card">
    {#if reviewSubmitted === false}
        <div class="icon-wrapper">
            <div class="icon">
                <img src={IconStar} alt="star icon" />
            </div>
        </div>
        <h1>How did we do?</h1>
        <p class="rating-request-message">
            Please let us know how we did with your support request. All
            feedback is appreciated to help us improve our offering!
        </p>
        <ul class="levels">
            {#each levels as level (level)}
                <li
                    class={`level ${selectedLevel === level ? "level--selected" : "level--nonselected"}`}
                >
                    <button
                        on:click={() => {
                            selectedLevel = level;
                        }}
                        type="button"
                    >
                        {level}
                    </button>
                </li>
            {/each}
        </ul>
        <button
            class="submit-btn"
            type="button"
            on:click={() => {
                if (selectedLevel > 0) {
                    reviewSubmitted = true;
                }
            }}>Submit</button
        >
    {:else}
        <div class="thank-you-illustration">
            <img src={ThankYouIllustration} alt="thank-you illustration" />
        </div>
        <p class="rating-submitted-score">
            You selected {selectedLevel} out of 5
        </p>
        <h1 class="thank-you-title">Thank you!</h1>
        <p class="rating-thank-you-message">
            We appreciate you taking the time to give a rating. If you ever need
            more support, don't hesitate to get in touch!
        </p>
    {/if}
</div>

<style>
    .card {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        padding: 1.6rem 1.5rem;
        align-items: center;
        background-color: var(--dark-blue);
        border-radius: 1rem;
        max-width: 360px;
    }
    .icon-wrapper {
        display: flex;
        width: 100%;
        justify-content: flex-start;
    }
    .icon {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 2.5rem;
        height: 2.5rem;
        border-radius: 999999px;
        background-color: var(--white-50);
    }

    .icon img {
        width: 0.8rem;
        height: 0.8rem;
    }
    h1 {
        color: var(--white);
        width: 100%;
        line-height: 150%;
        font-size: 1.5rem;
        font-weight: 700;
        align-self: flex-start;
    }
    .rating-request-message {
        margin-top: -0.5rem;
        font-size: 14px;
        color: var(--light-grey);
        line-height: 180%;
    }
    .levels {
        display: flex;
        gap: 1rem;
        width: 100%;
        justify-content: space-between;
    }
    .level {
        display: flex;
        width: 2.5rem;
        height: 2.5rem;
    }
    .level button {
        width: 100%;
        height: 100%;
        font-size: 14px;
        font-family: inherit;
        font-weight: 700;
        border-radius: 999999px;
        transition: all 150ms;
    }

    .level--selected button {
        background-color: var(--orange);
        color: var(--very-dark-blue);
    }

    .level--nonselected button {
        background-color: var(--white-50);
        color: var(--light-grey);
    }

    .level button:hover {
        background-color: var(--white);
        color: var(--very-dark-blue);
    }

    .submit-btn {
        margin-top: 0.5rem;
        width: 100%;
        border-radius: 999999px;
        text-transform: uppercase;
        background-color: var(--orange);
        font-weight: 700;
        color: var(--very-dark-blue);
        padding: 0.8rem;
        font-size: 14px;
        letter-spacing: 2px;
        font-family: inherit;
        transition: all 150ms;
    }

    .submit-btn:hover {
        background-color: var(--white);
        color: var(--very-dark-blue);
    }

    @media (min-width: 1440px) {
        .card {
            gap: 1.5rem;
            padding: 1.5rem 1.8rem;
            border-radius: 24px;
        }

        .rating-request-message {
            font-size: 13px;
            margin-top: -1rem;
        }

        .level {
            width: 2.7rem;
            height: 2.7rem;
        }

        .submit-btn {
            margin-top: 0;
            padding-block: 0.6rem;
        }
    }

    /* Thank you card; */
    .thank-you-illustration {
        margin-top: 0.5rem;
        width: 9rem;
        height: auto;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .thank-you-illustration img {
        width: 100%;
        height: 100%;
    }
    .thank-you-title {
        text-align: center;
    }
    .rating-submitted-score {
        margin-top: 0.5rem;
        margin-bottom: 0.5rem;
        color: var(--orange);
        font-size: 14px;
        background-color: var(--white-50);
        border-radius: 99999px;
        padding: 0.4rem 1rem;
        width: fit-content;
    }

    .rating-thank-you-message {
        margin-top: -0.5rem;
        margin-bottom: 0.5rem;
        text-align: center;
        font-size: 14px;
        line-height: 160%;
        color: var(--light-grey);
    }

    @media (min-width: 1440px) {
        /* Thank you card*/
        .rating-thank-you-message {
            font-size: 13px;
            margin-inline: 0.3rem;
            margin-top: -1rem;
        }
    }
</style>
