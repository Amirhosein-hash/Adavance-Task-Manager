<template>
    <div v-if="links.length > 3">
        <div class="flex flex-wrap -mb-1 justify-center">
            <template v-for="(link, key) in links">
                <div
                    v-if="link.url === null"
                    :key="key"
                    class="mb-1 mr-1 px-4 py-3 hover:bg-neutral-300 text-gray-400 text-sm leading-4 border rounded"
                    v-html="link.label"
                />
                <Link
                    v-else
                    :key="`link-${key}`"
                    class="mb-1 mr-1 px-4 py-3 hover:bg-neutral-300 focus:text-indigo-500 text-sm leading-4 border focus:border-indigo-500 rounded"
                    :class="{ 'bg-white': link.active }"
                    :href="link.url"
                    v-html="link.label"
                    :preserve-state="preserveState"
                    :method="method"
                />
            </template>
        </div>
    </div>
</template>

<script>
import { Link } from "@inertiajs/vue3";

export default {
    components: {
        Link,
    },
    props: {
        links: Array,
        preserveState: {
            type: Boolean,
            default: false,
        },
        method: {
            type: String,
            default: "get",
        },
    },
};
</script>
