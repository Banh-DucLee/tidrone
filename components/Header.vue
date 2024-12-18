<template>
    <header>
        <img class="header-logo" src="/images/Logo.png" alt="Logo de l'entreprise" />
        <nav class="desktop-nav">
            <ul>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/">Accueil</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/services">Mes Services</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/about">Qui suis-je ?</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/news">Mes Actualités</NuxtLink>
                </li>
                <li class="link-typo">
                    <NuxtLink class="header-link text-nowrap" to="/contact">Me Contacter</NuxtLink>
                </li>
            </ul>
        </nav>
    </header>
</template>

<style scoped>
    header {
        position: fixed;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        gap: 16px;
        width: 100%;
        margin: 0 auto;
        min-width: var(--width-min);
        max-width: var(--width-max);
        padding-inline: 16px;
        box-sizing: border-box;
        background-color: var(--color-primary-200);
        z-index: 999;
    }

    .header-logo {
        object-fit: contain;
        height: 80px;
        max-width: 50%;
    }

    .desktop-nav {
        flex: 1;
        max-width: 766px;
    }

    ul {
        margin: 0;
        padding: 0;
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        justify-content: space-between;
        list-style: none;
        text-decoration: none;
    }

    .header-link {
        text-decoration: none;
        color: var(--color-main-black);
    }

    .header-link:hover {
        color: var(--color-primary-500);
        text-decoration: underline;
    }

    @media (width <= 768px) {
        .desktop-nav {
            display: none;
        }
        
    }

</style>