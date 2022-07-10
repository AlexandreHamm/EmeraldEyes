<template>
    <h1 aria-label="title">
        EMERALD<span>EYES</span>
    </h1>
</template>

<style scoped>
h1{
    font-size: 8rem;
    color: var(--light);
    text-transform: uppercase;
    pointer-events: none;
    /* transform: translateY(100%);
    opacity: 0;
    transition: opacity 1s ease, transform 1s ease; */
}
h1::selection, span::selection{
    color: var(--light);
    background: transparent;
}
span, span::selection{
    color: var(--green);
}
/* @media (hover: hover){
    body:hover h1{
        transform: translate(0);
        opacity: 1;
        transition: opacity 1s ease, transform 1s ease;
    }
} */
@media screen and (orientation: portrait) {
  h1{
    font-size: 3rem;
    padding: 1rem;
  }
}
</style>