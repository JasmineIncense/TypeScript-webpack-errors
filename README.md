# TypeScript + webpack构建报错与解决方案集合

- ### TypeScript报错：Child process failed to process the request: Error: Debug Failure. False expression.

![图片.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/4189f221de874b1a9baa2570ce61b360~tplv-k3u1fbpfcp-watermark.image?)
在这里我使用了TypeScript v4.7.4的版本，导致报错。

解决方法：将typescript@4 的版本换成 typescript@3 的版本即可解决，npm i typescript@3 -D。现在使用的版本是v3.9.10。

---

- ### 错误 TS2717: Subsequent property declarations must have the same type.

![图片.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a6dc209373a549079edd8fe535fa0a81~tplv-k3u1fbpfcp-watermark.image?)
解决方法：在tsconfig.json配置 compilerOptions 中添加配置项 
`"skipLibCheck": true`。跳过声明文件`d.ts`的类型检查。

此配置有副作用，慎用！官方描述如下：

![图片.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0ea6e00e8ac34fab93551a38db8604da~tplv-k3u1fbpfcp-watermark.image?)
这可以节省编译期间的时间，但代价是类型系统的准确性。 例如，两个库可以以不一致的方式定义同一类型的两个副本。 TypeScript不会对所有的d.ts文件进行全面检查，而是会对你的应用在源代码中特别引用的代码进行输入检查。

---

- ### 错误 TS2613: Module '"*/node_modules/@types/*"' has no default export. | TS1259: Module '"*/node_modules/@types/*"' can only be default-imported using the 'esModuleInterop' flag
![图片.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5590c90dbb584fb4832c7da36d0ee654~tplv-k3u1fbpfcp-watermark.image?)
![图片.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/22288064ed1645f6bfd3623c0333ffa0~tplv-k3u1fbpfcp-watermark.image?)
解决方法：在tsconfig.json配置 compilerOptions 中添加配置项 "allowSyntheticDefaultImports": true。
官方描述如下：

![图片.png](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b29f5a47b69c4fd3b11a7f2d27fe9a4c~tplv-k3u1fbpfcp-watermark.image?)
