<template>
    <v-app>
        <v-app-bar
            app
            color="blue darken-4"
            dense
            dark
            height="40"
            clipped-left
            flat
        >
            <v-app-bar-nav-icon
                @click.stop="
                    () => {
                        drawer = !drawer;
                        temporary = !temporary;
                    }
                "
            ></v-app-bar-nav-icon>

            <v-toolbar-title>SysTools Customer Management</v-toolbar-title>

            <v-spacer></v-spacer>

            <v-avatar size="36" class="mr-2">
                <img
                    src="https://cdn.vuetifyjs.com/images/john.jpg"
                    alt="John"
                />
            </v-avatar>
            John Leider
        </v-app-bar>

        <v-navigation-drawer
            app
            v-model="drawer"
            permanent
            :mini-variant.sync="drawer"
            clipped
            hide-overlay
            :temporary="temporary"
            :class="{ temporary }"
        >
            <v-list dense>
                <v-list-item>
                    <v-list-item-icon>
                        <v-icon>mdi-home</v-icon>
                    </v-list-item-icon>

                    <v-list-item-title>Attractions</v-list-item-title>
                </v-list-item>

                <v-list-group>
                    <template v-slot:activator>
                        <v-list-item-icon>
                            <v-icon>mdi-account-circle</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>Customer</v-list-item-title>
                    </template>
                </v-list-group>

                <v-list-item>
                    <v-list-item-icon>
                        <v-icon>mdi-home</v-icon>
                    </v-list-item-icon>

                    <v-list-item-title>Order</v-list-item-title>
                </v-list-item>

                <v-list-item>
                    <v-list-item-icon>
                        <v-icon>mdi-home</v-icon>
                    </v-list-item-icon>

                    <v-list-item-title>User</v-list-item-title>
                </v-list-item>

                <v-list-group>
                    <template v-slot:activator>
                        <v-list-item-icon>
                            <v-icon>mdi-account-circle</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>Dining</v-list-item-title>
                    </template>
                </v-list-group>

                <v-list-item>
                    <v-list-item-icon>
                        <v-icon>mdi-home</v-icon>
                    </v-list-item-icon>

                    <v-list-item-title>Education</v-list-item-title>
                </v-list-item>

                <v-list-group>
                    <template v-slot:activator>
                        <v-list-item-icon>
                            <v-icon>mdi-account-circle</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>Family</v-list-item-title>
                    </template>
                </v-list-group>

                <v-list-group>
                    <template v-slot:activator>
                        <v-list-item-icon>
                            <v-icon>mdi-account-circle</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>Health</v-list-item-title>
                    </template>
                </v-list-group>

                <v-list-group>
                    <template v-slot:activator>
                        <v-list-item-icon>
                            <v-icon>mdi-account-circle</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>Office</v-list-item-title>
                    </template>
                </v-list-group>

                <v-list-group>
                    <template v-slot:activator>
                        <v-list-item-icon>
                            <v-icon>mdi-account-circle</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>Promotions</v-list-item-title>
                    </template>
                </v-list-group>
            </v-list>
        </v-navigation-drawer>

        <v-main>
            <v-container fluid class="pa-0">
                <v-card tile outlined>
                    <v-card-title>Customer</v-card-title>
                </v-card>

                <v-data-table
                    :headers="headers"
                    :items="customers"
                    show-select
                    hide-default-footer
                >
                    <template v-slot:top>
                        <v-row no-gutters align="center" class="border-bottom">
                            <v-col cols="2" class="px-2 py-1">
                                <v-text-field
                                    color="blue darken-4"
                                    placeholder="Search"
                                    outlined
                                    rounded
                                    dense
                                    append-icon="mdi-magnify"
                                    hide-details
                                ></v-text-field>
                            </v-col>

                            <v-col cols="auto">
                                <v-btn-toggle borderless group dense>
                                    <v-btn class="mx-1">
                                        <v-icon>mdi-format-align-right</v-icon>
                                    </v-btn>

                                    <v-btn class="mx-0 mr-1">
                                        <v-icon
                                            >mdi-format-align-justify</v-icon
                                        >
                                    </v-btn>
                                </v-btn-toggle>

                                <v-btn-toggle borderless mandatory dense group>
                                    <v-btn small class="ma-0">
                                        <v-icon>mdi-format-align-right</v-icon>
                                    </v-btn>

                                    <v-btn small class="ma-0">
                                        <v-icon
                                            >mdi-format-align-justify</v-icon
                                        >
                                    </v-btn>
                                </v-btn-toggle>
                            </v-col>

                            <v-col cols="auto">
                                <v-alert
                                    color="yellow darken-4"
                                    dismissible
                                    dense
                                    style="border-radius: 50px"
                                    class="my-2"
                                >
                                    Brand:
                                    <v-chip close small class="mx-1">
                                        Work
                                    </v-chip>
                                    <v-chip close small class="mx-1">
                                        Vacation
                                    </v-chip>
                                    <v-chip close small class="mx-1">
                                        Food
                                    </v-chip>
                                    <v-chip close small class="mx-1">
                                        Drawers
                                    </v-chip>
                                    <v-chip close small class="mx-1">
                                        Shopping
                                    </v-chip>
                                    <v-chip close small class="mx-1">
                                        Art
                                    </v-chip>
                                    <v-chip close small class="mx-1">
                                        Tech
                                    </v-chip>
                                </v-alert>
                            </v-col>

                            <v-spacer></v-spacer>

                            <v-col cols="auto">
                                <v-btn-toggle borderless dense group>
                                    <v-btn small class="ma-0">
                                        <v-icon>mdi-format-align-right</v-icon>
                                    </v-btn>
                                    <v-btn small class="ma-0">
                                        <v-icon
                                            >mdi-format-align-justify</v-icon
                                        >
                                    </v-btn>
                                    <v-btn small class="ma-0">
                                        <v-icon
                                            >mdi-format-align-justify</v-icon
                                        >
                                    </v-btn>
                                    <v-btn small class="ma-0">
                                        <v-icon
                                            >mdi-format-align-justify</v-icon
                                        >
                                    </v-btn>
                                    <v-btn small class="ma-0">
                                        <v-icon
                                            >mdi-format-align-justify</v-icon
                                        >
                                    </v-btn>
                                </v-btn-toggle>
                            </v-col>
                        </v-row>
                    </template>

                    <template v-slot:item.firstName="{ item }">
                        <a href="#">{{ item.firstName }}</a>
                    </template>
                </v-data-table>
            </v-container>
        </v-main>

        <v-footer app color="blue darken-4" dark>
            &copy; {{ new Date().getFullYear() }} -
            <a href="#" class="ml-1">SysTools</a>
        </v-footer>
    </v-app>
</template>

<script>
export default {
    name: "App",

    data: () => ({
        drawer: false,
        temporary: false,
        singleSelect: false,
        selected: [],
        headers: [
            { text: "First name", value: "firstName" },
            { text: "Last name", value: "lastName" },
            { text: "Email", value: "email" }
        ],
        customers: [
            {
                firstName: "M George",
                lastName: "Bluth",
                email: "george.bluth@reqres.in"
            },
            {
                firstName: "Janet",
                lastName: "Weaver",
                email: "janet.weaver@reqres.in"
            },
            {
                firstName: "Emma",
                lastName: "Wong",
                email: "emma.wong@reqres.in"
            },
            {
                firstName: "Eve",
                lastName: "Holt",
                email: "eve.holt@reqres.in"
            },
            {
                firstName: "Charles",
                lastName: "Morris",
                email: "charles.morris@reqres.in"
            }
        ]
    })
};
</script>

<style scoped>
.border-bottom {
    border-bottom: 1px solid rgba(0, 0, 0, 0.12);
}

.temporary {
    top: 40px !important;
}
</style>
