#### Example-02  - 加载自建模型

`GLTFLoader.js`提供了加载glf/glb模型的方法。

```js
// 绘制 - 自定义建模
let loader = new GLTFLoader();
loader.load('../static/test.glb',function(gltf){
    gltf.scene.position.set(0,0,-5);

    scene.add(gltf.scene);
},undefined,function(err){
    console.error(err);
});
```
`gltf` 标识自建模型的一个场景示例，将其添加到`scene`中作为组合元素。可以调用位置设定的方法。

##### 绘制线条

`LineBasicMaterial` 线条材质，设定颜色，通过设定经过的三维空间的点，来绘制`Vector3`
`Vector3`可以表示三维空间的点；动量、矢量表示等。