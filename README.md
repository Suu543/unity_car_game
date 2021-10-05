# unity_car_game

# Part-1 Settings
1. Unity Asset Store
2. Standard Assets (for Unity 2018.4)
<img src="https://cdn-images-1.medium.com/max/1200/1*dCmGTo9zhSYkVaw7i5YbGw.png" />
3. Package Manager - Standard Assets (Click Import)
<img src="https://cdn-images-1.medium.com/max/1200/1*nPchvKJotR-YBbrqwgRPfw.png" />
4. Import Mountain Race Tracks (Click Import)

# Part-2: Replace Car and Main Camera 
1. Snow mountain tracks ==> terrain (click and drag and drop)
- X 앞, Z 앞, Y 위

2. Standard Assets ==> Vehicles ==> Car ==> Prefabs ==> Car
- 1. Car을 맵위에 두고, 오른쪽 최상단에 layout ==> tall로 변경
- 2. Main Camera 위치 잡고, Car 자식요소로 넣어주기
- 3. 기존의 차를 멋이나는 람보르기니 등으로 변경해보자
  - https://assetstore.unity.com/packages/3d/vehicles/land/60-fantastic-race-cars-pack-45149
  - https://drive.google.com/u/0/uc?id=1-6hRUWZkLCjvlwWHyI3h3y59q0biv_ZQ&export=download
- 4. import - 60 fantastic race cars pack  
- 5. Res ==> Cars ==> AE_CARS ==> SAMOCHODY ==> Car_23 ==> Full Prefab
- 6. 기존의 Car에 붙여 넣고 Overlap 되도록 만들기 ==> 이름 변경 (Lamborghini)
- 7. Car 자식 요소 중 SkyCar 찾아서 Checkbox 해제 ==> Lamborghini를 Car의 자식 요소로 만들기
- 8. Car Wheel Meshes에서 Element 0 ~ 3을 모두 Lamborghini의 바퀴 요소로 변경하기
    - Element 0 ==> Wheel_R
    - Element 1 ==> Wheel_L
    - Element 2 ==> Wheel_Back_R
    - Element 3 ==> Wheel_Back_L
- 9. 바퀴 형태가 조금 이상할 경우, Car ==> WheelsHubs의 각 바퀴를 규격에 맞게 조정하면된다.
- 10. Main Camera는 이제 Car 자식에서 밖으로 빼고 scripts 폴더 만들기 ==> MainCamera C# 파일 생성
- 11. Main Camera에 ==> MainCameraMovement Script 붙여넣기
- 12. Car을 Main Camera Movement Script Target에 삽입하기
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MainCameraMovement: MonoBehaviour
{
    public Transform target;
    public float distance = 6.0f;
    public float height = 3.0f;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        // if (target == null) return;
        transform.position = target.position;
        transform.position = transform.position - target.rotation * Vector3.forward * distance;
        transform.position = new Vector3(transform.position.x, transform.position.y + height, transform.position.z);
        transform.LookAt(target);
    }
}

```

- 13. Asset Store ==> Skybox ==> Import
<img src="https://cdn-images-1.medium.com/max/1200/1*_dlcKjZug8evzZltzH-9hg.png" />
- 14. Main Camera ==> Add Component ==> Skybox ==> Assets (SkySerie Freebie) 중에 하나 고르기
