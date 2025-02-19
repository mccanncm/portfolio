<template>
  <div 
    class="item" 
    @click="toggleExpanded"
    :class="{ expanded: isExpanded }">
    <i
      :class="{ hovered: isHovered }"
      @mouseover="isHovered = true"
      @mouseleave="isHovered = false"
    >
      <slot name="icon"></slot>
    </i>
    <div class="details">
      <h3>
        <slot name="heading"></slot>
      </h3>
      <div class="content-wrapper">
          <slot name="content">hello</slot>
        </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data(): { 
    isHovered: boolean,
    isExpanded: boolean,
  } {
    return {
      isHovered: false, // Tracks the hover state
      isExpanded: false, // Tracks the expanded state
    };
  },
  methods: {
    toggleExpanded(){
      this.isExpanded = !this.isExpanded;
    },
  },
};
</script>

<style scoped>
  .item {
    margin-top: 2rem;
    display: flex;
    position: relative;
  }

  .details {
    flex: 1;
    margin-left: 1rem;
  }

  i {
    display: flex;
    place-items: center;
    place-content: center;
    width: 32px;
    height: 32px;
    color: var(--color-text);
    transition: transform 0.3s, background-color 0.3s;
  }

  i.hovered {
    transform: scale(1.2); /* Enlarges the icon slightly */
    background-color: var(--color-highlight); /* Add a background color */
    color: var(--color-text-hover); /* Change text color */
    background-color: #52645c;
    border-radius: 8px;
  }

  h3 {
    font-size: 1.2rem;
    font-weight: 500;
    margin-bottom: 0.4rem;
    color: var(--color-heading);
  }

  /* Content Wrapper for transition */
  .content-wrapper {
    overflow: hidden; /* Hide overflowing content when collapsed */
    max-height: 0; /* Initially collapsed */
    transition: max-height 0.5s ease-in-out;
    
  }

  .item .content-wrapper {
    max-height: 0; /* Initially collapsed */
  }

  .item.expanded .content-wrapper {
    max-height: 750px; /* Adjust based on your content size */
    overflow-y: scroll;
    scrollbar-width: thin;
    scrollbar-color: #52645c #f5f5f5; /* For Firefox */
    scrollbar-width: none; /* Hides the scrollbar arrows */
  }

  @media (min-width: 1024px) {
    .item {
      margin-top: 0;
      padding: 0.4rem 0 1rem calc(var(--section-gap) / 2);
    }

    i {
      top: calc(50% - 25px);
      left: -26px;
      position: absolute;
      border: 1px solid var(--color-border);
      background: var(--color-background);
      border-radius: 8px;
      width: 50px;
      height: 50px;
    }

    .item:before {
      content: ' ';
      border-left: 1px solid var(--color-border);
      position: absolute;
      left: 0;
      bottom: calc(50% + 25px);
      height: calc(50% - 25px);
    }

    .item:after {
      content: ' ';
      border-left: 1px solid var(--color-border);
      position: absolute;
      left: 0;
      top: calc(50% + 25px);
      height: calc(50% - 25px);
    }

    .item:first-of-type:before {
      display: none;
    }

    .item:last-of-type:after {
      display: none;
    }
  }
</style>
