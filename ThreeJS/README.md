# ThreeJS 맛보기
### 3D 모델 가져오기
- Sketchfab 에서 원하는 모델을 선택해서 다운로드해준다.
- glTF 포함파일 선택

### npm 설치
- vue나 react 프로젝트면 설치는 npm install three.
- 그냥 html 파일이라면 아래의 코드 두가지를 작성해주면된다.
```jsx
    <script type="importmap">
        {
            "imports": {
                "three": "https://unpkg.com/three@0.141.0/build/three.module.js",
                "GLTFLoader" : "https://unpkg.com/three@0.141.0/examples/jsm/loaders/GLTFLoader.js"
            }
        }
    </script>
```
- npm 설치와 동일한 기능을 완성해주는 코드

```jsx
    <script tyle="module">
        import {GLTFLoader} from 'GLTFLoader';
        import * as THREE from 'three';
    </script>
```
- import 해주는 코드

### 3D 모델 브라우저에 보여주는 법
1. 장면을 만들고
2. 브라우저에 렌더링해달라고 요구하면 끝

### 3D 모델을 보여줄 때 필요한 것들
1. 카메라
    - 카메라 세팅방법
    - `let camera = new THREE.PerspectiveCamera(30, 1);`
    - 카메라 종류는 2가지
        - PerspectiveCamera (원근법 O)
        - OrthographicCamera (원근법 무시)
2. 조명
    - 조명 세팅방법
    - `let light = new THEREE.DirectionalLight(0xffff00, 10);`
    - `scene.add(light);`
    - 조명 종류는 다음과 같다
        - AmbientLight
        - PointLight
        - DirectionalLight
3. 배경
    - 배경 세팅방법
    - `scene.background = new THREE.Color('white');`

### 3D 모델 애니메이션
- 로드 함수의 콜백함수 내부에 작성해준다.
```jsx
    function animate() { // 애니메이션 주기 (ex 오브젝트 회전)
        requestAnimationFrame(animate)
        gltf.scene.rotation.y += 0.01 // y축으로 회전시켜주기
        renderer.render(scene, camera);
    }
    animate() // 함수 불러오기
```

### 마우스컨트롤?
- Three.js 내의 OrbitControl 을 사용하면 마우스로 해당 오브젝트를 컨트롤 할 수 있다.