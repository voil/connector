![alt text](https://files.fm/thumb_show.php?i=e8jj6wa82 "Title")

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
| position |✅ | PositionType|---- | Position of element. | 
| canRemove |❌ | boolean | false | Property that determines whether an element can be deleted. |
| canMove |❌ | boolean | false | Property that determines whether an element can be moved. |
| connectorsPositions|❌ | ConnectorsPositions | ---- | Property that determines which connector show. |
| connectionType |❌ | 'number', 'text', 'boolean', 'select' | ---- | Property that determines of connection type elements. |
| additionalOptions |❌ | any | ---- | Additionals options of element. |
| groups |❌ | string[] | ---- | Property that specifies which group the item belongs to. |
| canConnectGroup |❌ | string[] | ---- | Property that specifies which group can connect element. |
| connectionTypeSelectOptions |❌ | ConnectionTypeSelectOptionsType | ---- | Property that specifies of select types for connection value. |

### Element properties types:
| Type name | properties | type |
|-----------|------------|------|
| PositionType| { x: number, y: number }, | object |
| ConnectionTypeSelectOptionsType | { lable: string, value: number, string, boolean } | object |
| ConnectorsPositions | LEFT, RIGHT, BOTTOM, TOP | enum |


## IvrElement component arguments:
| Argument name | required | type | description |
| ------------- | :--------: | ---- | ----------- |
| currentElement | ✅ | ElementType | Current element |.

## IvrContent component arguments:
| Argument name | required | type | description |
| ------------- | :--------: | ---- | ----------- |
| ivrScheme | ✅| SchemeTypeProp | Main scheme of ivr tree. |
| isZoomActive | ❌| boolean | Is zoom plugin for Ivr tree is active. |
| isAutoSaveActive|❌ | boolean | Is auto save plugin for Ivr tree is active. |
| isRevisionActive | ❌ | boolean | Is revision plugin for Ivr tree is active. |
| withAnimation |❌ | boolean | Is animation for Ivr tree is active. |
| autoSaveDuration |❌ | number | Duration time for auto save plugin |
| isFullscreenActive | | boolean | Is full screen plugin for Ivr tree is active. |
| isMiniMapActive | | boolean | Is mini map plugin fo Ivr tree is active

### IvrContent component events methods:
| Event name | required | arguments | description |
| ---------- | -------- | --------- | ----------- |
| onUpdate | ❌ | SchemeIvrTypeProp | Event fired when Ivr scheme updated |
| onAutoSave | ❌ | ---- | Event fired when auto save plugin is active |








