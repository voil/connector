## Install
```shell
yarn add voil/connector
```

## Quick Start
``` javascript
<template>
  <IvrContent
    :ivr-scheme="scheme"
    @onUpdate="handleUpdateIvrScheme"
  >
    <template #elementsList="slotProps">
      <IvrElement
        :key="element.uniqueId"
        :currentElement="element"
        v-for="element in Object.values(slotProps.elements)"
      >
        <template #content>
          <div>element</div>
        </template>
      </IvrElement>
    </template>
  </IvrContent>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import {
  IvrContent,
  IvrElement,
  SchemeIvrTypeProp,
} from 'voil/connector';

export default defineComponent({
  name: 'App',
  components: {
    IvrContent,
    IvrElement,
  },
  setup() {
    const scheme = reactive<SchemeIvrTypeProp>({
        elements: [{
          uniqueId: 'element1',
          position: {
            x: 700,
            y: 100,
          },
          canMove: true,
          canRemove: true,
        }],
        paths: [],
    });
    return {
      scheme,
      handleUpdateIvrScheme: (updatedScheme: SchemeIvrTypeProp) => {
        scheme.elements = updatedScheme.elements;
        scheme.paths = updatedScheme.paths;
      },
    };
  },
});
</script>
```
