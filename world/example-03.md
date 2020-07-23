### Example-03  - 场景绘制及场景控制


#### 场景布置 - Scene

`Scene` 继承自`Object3D`的属性、方法。

`Scene`自己的属性说明：

* `background` 当前场景的背景色。
* `Fog` Fog(color,near,far)示例 摄像机角度之外的部分的展示情况。距离摄像机距离 len > near&&len < far 部分影响。

### 灯光架设 
#### 半球光HemisphereLight

半球光示例创建。
`HemisphereLight( skyColor, groundColor, intensity)`天空中发出光线的颜色; 地面发出光线的颜色;光照强度。

#### 平行光 DirectionalLight

DirectionalLight( color, intensity )光的颜色、光的强度。

`shandow` DirectionalLightShadow示例，用于计算阴影。

### 平面场景

用于直观表现立体物体位置关系、展现阴影效果。

```js
// ground
var ground = new THREE.Mesh( new THREE.PlaneBufferGeometry( 2000, 2000 ), new THREE.MeshPhongMaterial( { color: 0x999999, depthWrite: false } ) );
// 调整方向、平面展示
ground.rotation.x = - Math.PI / 2;
// 接收阴影展示
ground.receiveShadow = true;
scene.add( ground );

var grid = new THREE.GridHelper( 2000, 20, 0x000000, 0x000000 );
grid.material.opacity = 0.2;
grid.material.transparent = true;
scene.add( grid );
```
属性说明：

* `PlaneBufferGeometry` 生成几何平面的接口，接收参数执行x方向的宽度、y轴方向的宽度。
* `MeshPhongMaterial` 表面高光、高亮的材质。组合平面结构生成物体示例。

### 控制

`OrbitControls` 摄像机围绕物体旋转。不同方向观察；

### 窗口控制

浏览器窗口大小变化时，进行重绘。

```js
function onWindowResize() {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize( window.innerWidth, window.innerHeight );
}
```