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

## Element properties
| Properties name | Required | Type | Default value | Descrption |
| --------------- | :---------:| ---- | :-------------: | ---------- |
| uniqueId |✅ | string | ---- | Unique id of element. |
| position |✅ | { x: number, y: number } | ---- | Position of element. | 
| canRemove |❌ | boolean | false | Property that determines whether an element can be deleted. |
| canMove |❌ | boolean | false | Property that determines whether an element can be moved. |
| connectorsPositions|❌ | ConnectorsPositions | ---- | Property that determines which connector show. |
| connectionType |❌ | 'number', 'text', 'boolean', 'select' | ---- | Property that determines of connection type elements. |
| additionalOptions |❌ | any | ---- | Additionals options of element. |
| groups | | string[] | ---- | Property that specifies which group the item belongs to. |
| canConnectGroup |❌ | string[] | ---- | Property that specifies which group can connect element. |
| connectionTypeSelectOptions |❌ | ConnectionTypeSelectOptionsType | ---- | Property that specifies of select types for connection value. |
