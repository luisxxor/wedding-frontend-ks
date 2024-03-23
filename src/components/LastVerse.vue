<template>
    <div class="lastVerseContainer">
    </div>
</template>

<script lang="ts">
    async function wait(ms: number) {
        return new Promise(resolve => setTimeout(resolve, ms));
    }

    export default {
        name: 'LastVerse',
        data: () => ({
            verse: '',
        }),
        mounted() {
            // Call writeText as a callback of intersection observer
            const options = {
                root: null,
                rootMargin: '0px',
                threshold: 0.5,
            };

            const callback = (entries: IntersectionObserverEntry[]) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        this.writeText();
                    }
                });
            };

            const observer = new IntersectionObserver(callback, options);

            observer.observe(this.$el);
        },
        methods: {
            async writeText() {
                const verseSource = `El amor es sufrido, es benigno; el amor no tiene envidia, el amor no es jactancioso, no se envanece; no hace nada indebido, no busca lo suyo, no se irrita, no guarda rencor; no se goza de la injusticia, mas se goza de la verdad. Todo lo sufre, todo lo cree, todo lo espera, todo lo soporta. El amor nunca deja de ser; pero las profecías se acabarán, y cesarán las lenguas, y la ciencia acabará.`;
                
                while (this.verse.length < verseSource.length) {
                    this.verse += verseSource[this.verse.length];

                    let waitingTime = 50;

                    if (['.', ',', ';'].includes(this.verse[this.verse.length - 1])) {
                        waitingTime = 500;
                    }

                    await wait(waitingTime);
                }

                setTimeout(() => {
                    const $el = this.$refs.verseRef

                    if ($el instanceof Element) {
                        $el.classList.remove('hidden');
                    }
                    
                }, 500);
            },
        },
    }
</script>

<style>
    .lastVerseContainer {
        margin-top: 6rem;
        padding: 1rem;
        font-family: 'Roboto', sans-serif;
        font-weight: 300;
        letter-spacing: 2px;
        text-align: justify;
        line-height: 1.5rem;
        font-size: .8rem;
    }

    .verse-ref {
        text-align: right;
        font-size: .7rem;
        font-weight: 300;
        margin-top: 1rem;
        transition: opacity 1s;
    }

    .hidden {
        opacity: 0;
    }

    @media (min-width: 768px) {
        .lastVerseContainer {
            margin-top: 8rem;
            font-size: 1em;
            font-weight: 500;
        }

        .verse-text > p {
            height: 120px;
        }

        .verse-ref {
            font-size: .9rem;
            height: 24px;
        }
    }
</style>