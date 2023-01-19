<template>
    <div class="container-fluid">
        <div class="row align-items-start">
            <div class="sidebar col-auto order-first d-print-none">
                <nav>
          <span class="navbar-brand">
            <inertia-link
                href="/"
                class="d-inline-block text-center text-decoration-none"
            >
                <application-logo/>
            </inertia-link>
          </span>
                    <template v-if="$page.props.user">
                        <div class="nav-item">
                            <inertia-link
                                class="nav-link"
                                :href="'/'"
                            >
                                <span class="nav-item-title align-top d-inline-block">
                  Nav 1
                </span>
                            </inertia-link>
                        </div>

                        <hr />
                        <div v-if="$page.props.nav.updateTeam" class="nav-item">
                            <inertia-link
                                class="nav-link"
                                :class="{
                  active: route().current('teams.show', [$page.props.team.id]),
                }"
                                :href="route('teams.show', [$page.props.team.id])"
                            >
                <span class="nav-item-title align-top d-inline-block"
                >Team</span
                >
                            </inertia-link>
                        </div>
                        <div class="nav-item">
                            <inertia-link
                                class="nav-link"
                                :class="{ active: route().current('profile.show') }"
                                :href="route('profile.show')"
                            >
                                <span class="nav-item-title d-inline-block">Profile</span>
                            </inertia-link>
                        </div>
                        <div class="nav-item">
                            <inertia-link
                                class="nav-link"
                                method="post"
                                :href="route('logout')"
                            >
                                <span class="nav-item-title d-inline-block">Logout</span>
                            </inertia-link>
                        </div>

                    </template>
                </nav>
            </div>
            <main class="col">
                <header class="container">
                    <h2 class="page-header"><slot name="page-header"></slot></h2>
                    <p class="page-subheader"><slot name="page-subheader"></slot></p>
                </header>
                <section class="container page-section">
                    <slot></slot>
                </section>
            </main>
        </div>
    </div>

</template>

<script>
import ApplicationLogo from "../Components/ApplicationLogo";
export default {
    props:{

    },
    components: {
        ApplicationLogo
    },
    methods: {

    },
}
</script>
