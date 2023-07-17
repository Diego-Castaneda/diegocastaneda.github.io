<article class="post-card">
    <!-- svelte-ignore a11y-missing-attribute -->
    <div class="image"><slot name="image"></slot></div>
    <div class="content">
        <h1 class="title"><slot name="title"></slot></h1>
        <aside><span class="accent"><slot name="readtime"></slot></span></aside>
        <main><slot name="description"></slot></main>
        <div class="tags"><slot name="tags"></slot></div>
    </div>
</article>

<style>
    article {
        display: flex;
        flex-direction: column;
        align-items: start;
        border-radius: 10px;
        background-color: white;
        box-shadow: 0 0 10px 3px rgba(133, 132, 132, 0.1);

        transition: transform 500ms ease;
    }

    article:hover {
        transform: scale(1.01);
        box-shadow: 0 0 20px 10px rgba(49, 48, 48, 0.1);
    }

    .content {
        padding: 1rem;
        display: flex;
        flex-direction: column;
        align-items: start;
    }

    .image {
        overflow: hidden;
    }

    .accent {
        font-weight: 300;
        opacity: 70%;
    }
</style>