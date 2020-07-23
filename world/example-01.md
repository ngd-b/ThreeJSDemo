#### Example-01  - 绘制了一个旋转的立方体

`threeJS.js`提供所有绘制3d图形使用到的核心API。

对示例中的做说明：

1. `Scene`场景：类似于canvas 2d的画布，这个是3d,叫场景。用于布局你想要放置的东西，包括灯光、摄像机、物体。
2. `PerspectiveCamera`摄像机：物体的观察者，呈现给用户的就是观察到的东西。常用透视摄像机`PerspectiveCamera`.
3. `WebGLRenderer`渲染器，以上都是你在代码层面做的设计，需要成现在上，则需要渲染器。输出一个`canvas`元素对象添加到HTML文档中。
4. `Mesh` 实例化一个物体，`BoxGeometry`指的是立方体结构；`MeshBasicMaterial`指的是物体材质。两者构成一个实体物体。然后添加到场景中。
5. 函数`animate`的作用，如果我们不创建这个函数，直接渲染到页面上。页面展示的是一个平面的长方形。通过`requestAnimationFrame(animate)`重复刷新渲染帧，可以做一些改变物体顺序性的操作(让他旋转起来)。
    ```js
        let render = new THREE.WebGLRenderer();
        render.setSize(window.innerWidth,window.innerHeight);
        document.body.appendChild(render.domElement);
        // 直接渲染
        render.render(scene,camera);
        
        function animate(){
            requestAnimationFrame(animate);
            // 使物体旋转
            cube.rotation.x+=0.01;
            cube.rotation.y+=0.01;
            
            render.render(scene,camera);
        }
        // animate();
    ```
效果:

<img src="https://github.com/ngd-b/ThreeJSDemo/blob/master/static/images/example-01.gif" width="500" />