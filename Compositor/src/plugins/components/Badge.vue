<script setup lang="ts">
// Badge.vue
// This component is a simple badge that can be used to display status or information.
// It supports different types and can trigger an event when clicked.
// The types are defined in BadgeTypes.ts.

import { badgeTypes, type BadgeType } from './BadgeTypes';

interface BadgeProps {
    attachEvent?: boolean;
    type?: BadgeType;
}

const props = withDefaults(defineProps<BadgeProps>(), {
    attachEvent: true,
    type: 'primary'
});

const raiseAlert = (): void => {
    alert('you have clicked the badge');
};
</script>

<template>
    <div class="badge" :class="`badge-${props.type}`" @click.self.stop="props.attachEvent ? raiseAlert : undefined">
        <slot></slot>
    </div>
</template>

<style scoped>
.badge {
    display: inline-block;
    text-shadow: #000000 0 1px 1px;


    padding: 0.1lh 1ch;
    border-radius: 0.25em;
    color: white;
    font-weight: bold;
}

.badge-married {
    background-color: #ff69b4;
    /* Pink color for married badge */
}

.badge-single {
    background-color: #4575b8;
    /* Orange color for single badge */
}

.badge-primary {
    background-color: #007bff;
}

.badge-secondary {
    background-color: #6c757d;
}

.badge-success {
    background-color: #28a745;
}

.badge-danger {
    background-color: #dc3545;
}

.badge-warning {
    background-color: #ffc107;
}

.badge-info {
    background-color: #17a2b8;
}

.badge:hover {
    opacity: 0.8;
}

.badge:active {
    opacity: 0.6;
}

.badge:focus {
    outline: none;
    box-shadow: 0 0 0 0.2em rgba(0, 123, 255, 0.25);
}

.badge:focus-visible {
    outline: 2px solid #007bff;
    outline-offset: 0.25em;
}

.badge:focus:not(:focus-visible) {
    outline: none;
}

.badge:disabled {
    opacity: 0.65;
    cursor: not-allowed;
}

.badge:disabled:hover {
    opacity: 0.65;
}

.badge:disabled:active {
    opacity: 0.65;
}

.badge:disabled:focus {
    outline: none;
    box-shadow: none;
}

.badge:disabled:focus-visible {
    outline: none;
}

.badge:disabled:focus:not(:focus-visible) {
    outline: none;
}
</style>
