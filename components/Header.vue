<template>
    <header>
        <NuxtLink class="header-logo" to="/">
            <img class="header-logo-image" src="/images/svg/logo_dark.svg" alt="Logo de l'entreprise" />
        </NuxtLink>
        <nav class="desktop-nav">
            <ul>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/">Accueil</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/services">Services</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/about">Qui suis-je ?</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/news">Actualités</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/contact">Contact</NuxtLink>
                </li>
            </ul>
        </nav>
        <Button class="header-cta" buttonType="redirect" text="Contactez nous" to="/contact" buttonClass="button-typo-large" />
    </header>
</template>

<style scoped>
    header {
        position: fixed;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
        width: 100%;
        margin: 0 auto;
        min-width: var(--width-min);
        max-width: var(--width-max);
        padding-inline: 16px;
        box-sizing: border-box;
        background-color: var(--color-main-black);
        z-index: 999;
        color: var(--color-main-white);
    }

    .header-logo {
        height: 80px;
        max-width: 50%;
    }

    .header-logo-image {
        object-fit: contain;
        height: 100%;
    }

    .desktop-nav {
        flex: 1;
        padding: 12px 0;
        border-radius: 5px;
        max-width: 766px;
    }

    ul {
        margin: 0;
        padding: 0;
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        justify-content: space-evenly;
        list-style: none;
        text-decoration: none;
    }

    .header-link {
        text-decoration: none;
        color: var(--color-main-white);
    }

    .header-link:hover {
        color: var(--color-primary-500);
        text-decoration: underline;
    }

    @media (width <= 768px) {
        .desktop-nav {
            display: none;
        }
        
        .header-cta {
            display: none;
        }
    }

</style>