<template>
    <footer>
        <div v-if="hasTopSection === true" class="footer-top">
            <div class="footer-top-text">
                <h4 class="title-4">Contactez-moi dès maintenant !</h4>
                <p class="text-sm">Lorem ipsum odor amet, consectetuer adipiscing elit. Aaliquet fames netus rutrum nisi accumsan. Nam molestie placerat cras ut quisque</p>
            </div>
            <div class="footer-top-cta">
                <Button buttonType="mail" text="Par Mail" to="contact@tidrone.fr" buttonStyle="button-typo-large" />
                <Button buttonType="redirect" text="Via Formulaire" to="/contact" buttonStyle="button-typo-large" />
            </div>
        </div>
        <div class="footer-bottom">
            <div class="footer-bottom-nav-container">
                <p class="paragraph-regular text-center">Besoin de plus d'informations ? Naviguez facilement parmi les pages pour découvrir mes prestations et me contacter</p>
                <nav>
                    <ul class="footer-bottom-nav">
                        <li><NuxtLink class="link-typo footer-bottom-nav-link" to="/">Accueil</NuxtLink></li>
                        <li><NuxtLink class="link-typo footer-bottom-nav-link" to="/services">Mes Services</NuxtLink></li>
                        <li><NuxtLink class="link-typo footer-bottom-nav-link" to="/about">Qui suis-je ?</NuxtLink></li>
                        <li><NuxtLink class="link-typo footer-bottom-nav-link" to="/news">Mes Actualités</NuxtLink></li>
                        <li><NuxtLink class="link-typo footer-bottom-nav-link" to="/contact">Me Contacter</NuxtLink></li>
                    </ul>
                </nav>
            </div>
            <div class="footer-bottom-socials">
                <p class="text-sm text-center text-nowrap">Retrouvez-moi sur :</p>

            </div>
            <div class="footer-bottom-logo-container">
                <img class="footer-bottom-logo" src="/images/Logo.png" alt="Logo de l'entreprise">
                <p class="text-sm footer-bottom-copyright">© 2024 Tous droits réservés</p>
            </div>
        </div>
    </footer>
</template>

<script setup>
defineProps({
    hasTopSection: {
        type: Boolean,
        default: true,
    }
});
</script>

<style scoped>
    footer {
        display: flex;
        flex-flow: column nowrap;
        box-sizing: border-box;
        width: 100%;
    }

    .footer-top {
        width: 100%;
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        justify-content: space-between;
        gap: 8px;
        box-sizing: border-box;
        padding: 32px 16px;
        background-color: var(--color-opacity-primary-20);
    }

    .footer-top-text {
        width: 50%;
    }

    .footer-top-cta {
        flex: 1;
        display: flex;
        flex-flow: row wrap;
        align-items: center;
        justify-content: space-evenly;
        gap: 32px;
    }

    .footer-bottom {
        width: 100%;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-evenly;
        padding: 16px;
        box-sizing: border-box;
        gap: 16px;
        background-color: var(--color-opacity-primary-50);
    }

    .footer-bottom-nav-container {
        display: flex;
        flex-flow: column nowrap;
        justify-content: space-evenly;
        gap: 8px;
    }

    .footer-bottom-nav {
        width: 100%;
        display: flex;
        flex-flow: row wrap;
        align-items: center;
        justify-content: space-around;
        list-style: none;
        gap: 12px;
        margin: 0;
        padding: 0;
    }

    .footer-bottom-nav-link {
        text-decoration: none;
        color: var(--color-main-black);
    }

    .footer-bottom-socials {
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        justify-content: space-evenly;
    }

    .footer-bottom-logo-container {
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        justify-content: space-between;
        gap: 8px;
    }

    @media (width <= 768px) {
        .footer-bottom {
            flex-direction: column;
            gap: 32px;
        }

        .footer-bottom-nav-container {
            gap: 24px;
        }
    }
</style>