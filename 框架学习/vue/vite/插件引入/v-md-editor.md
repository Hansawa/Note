```js
/* src/plugins/v-md-editor.js */

/* markdown编辑显示器 */
import VMEditor from '@kangc/v-md-editor/lib/codemirror-editor'
import '@kangc/v-md-editor/lib/style/codemirror-editor.css'
// codemirror 编辑器的相关资源
import Codemirror from 'codemirror';
// mode
import 'codemirror/mode/markdown/markdown';
// placeholder
import 'codemirror/addon/display/placeholder';
// active-line
import 'codemirror/addon/selection/active-line';
// scrollbar
import 'codemirror/addon/scroll/simplescrollbars';
import 'codemirror/addon/scroll/simplescrollbars.css';
// style
import 'codemirror/lib/codemirror.css';

/* markdown预览器 */
import VMPreview from '@kangc/v-md-editor/lib/preview'
import '@kangc/v-md-editor/lib/style/preview.css'

/* 引入主题 */
import VuepressTheme from '@kangc/v-md-editor/lib/theme/vuepress'
import '@kangc/v-md-editor/lib/theme/style/vuepress.css'

VMEditor.Codemirror = Codemirror;
VMEditor.use(VuepressTheme);

VMPreview.use(VuepressTheme);

export default (app) => {
    app.use(VMEditor);
    app.use(VMPreview);
};
```
