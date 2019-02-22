
## 
```raw
src
├── directives
│   ├── async-append.ts
│   ├── async-replace.ts
│   ├── cache.ts
│   ├── class-map.ts
│   ├── guard.ts
│   ├── if-defined.ts
│   ├── repeat.ts
│   ├── style-map.ts
│   ├── unsafe-html.ts
│   └── until.ts
├── env.d.ts
├── lib
│   ├── default-template-processor.ts  // 默认的template processor
│   ├── directive.ts            // 
│   ├── dom.ts
│   ├── modify-template.ts      // 
│   ├── part.ts                 // 定义了part的基础interface行为
│   ├── parts.ts                // 定义了各种基类的 parts
│   ├── render-options.ts       // 定义了如何render的options.
│   ├── render.ts               // 
│   ├── shady-render.ts         //
│   ├── template-factory.ts     // 用于创建template的, 底层会用缓存去cache创建出来的Template.
│   ├── template-instance.ts    // 用于插入在dom节点之后的live update, 工作机制还是需要再详细理解下.
│   ├── template-processor.ts   // 没有特别懂是怎么回事
│   ├── template-result.ts      // TemplateResult, 没怎么看懂, 就是创建了一个template节点, 然后在对应的节点插入了nodeMarker节点.
│   └── template.ts             // Template, 会根据 html tag string 处理掉的 TemplateResult 返回 Template. 会在对应的节点生成part分割.
├── lit-html.ts
├── polyfills
│   └── template_polyfill.ts
```

## 解释

* `part`: 每个可以commit的最小分类. 属性, 节点Node, property 等等
  * `nodePart `: 会在startNode到endNode之间做操作, 删减node节点
* `html`: tag template 会将字符串转换成`TemplateResult`返回.
* `TemplateFactory`: `export type TemplateFactory = (result: TemplateResult) => Template;`
* `TemplateInstance`: 用于负责更新 template 和 values 的主要 class. 需要详细阅读下. 



# Links
* [How To Traverse the DOM](https://www.digitalocean.com/community/tutorials/how-to-traverse-the-dom)
* [DOM tree](https://javascript.info/dom-nodes)






> ## 🛠 Status: In Development
> lit-html is currently in development. It's on the fast track to a 1.0 release, so we encourage you to use it and give us your feedback, but there are things that haven't been finalized yet and you can expect some changes.

# lit-html
Efficient, Expressive, Extensible HTML templates in JavaScript

[![Build Status](https://travis-ci.org/Polymer/lit-html.svg?branch=master)](https://travis-ci.org/Polymer/lit-html)
[![Published on npm](https://img.shields.io/npm/v/lit-html.svg)](https://www.npmjs.com/package/lit-html)
[![Mentioned in Awesome lit-html](https://awesome.re/mentioned-badge.svg)](https://github.com/web-padawan/awesome-lit-html)

## Documentation

Full documentation is available at [lit-html.polymer-project.org](https://lit-html.polymer-project.org).

Docs source is in the `docs` folder. To build the site youself, see the instructions in [docs/README.md](docs/README.md).

## Overview

`lit-html` lets you write [HTML templates](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/template) in JavaScript with [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).

lit-html templates are plain JavaScript and combine the familiarity of writing HTML with the power of JavaScript. lit-html takes care of efficiently rendering templates to DOM, including efficiently updating the DOM with new values.

```javascript
import {html, render} from 'lit-html';

// This is a lit-html template function. It returns a lit-html template.
const helloTemplate = (name) => html`<div>Hello ${name}!</div>`;

// This renders <div>Hello Steve!</div> to the document body
render(helloTemplate('Steve'), document.body);

// This updates to <div>Hello Kevin!</div>, but only updates the ${name} part
render(helloTemplate('Kevin'), document.body);
```

`lit-html` provides two main exports:

 * `html`: A JavaScript [template tag](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals) used to produce a `TemplateResult`, which is a container for a template, and the values that should populate the template.
 * `render()`: A function that renders a `TemplateResult` to a DOM container, such as an element or shadow root.

## Installation

```bash
$ npm install lit-html
```

## Status

`lit-html` is under active development and has not yet had a 1.0 release. The
internal API may still change somewhat. The `html` and `render` API is stable.

## Contributing

Please see [CONTRIBUTING.md](./CONTRIBUTING.md).
