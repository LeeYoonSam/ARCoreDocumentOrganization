# ARCore 클래스 설명

## **com.google.ar.core**
## [Anchor](https://developers.google.com/ar/reference/java/com/google/ar/core/Anchor)
> public class Anchor

* 실제 세계에서 고정 된 위치와 방향을 설명합니다. 실제 공간에서 고정 된 위치에 머물기 위해 공간에 대한 ARCore의 이해가 향상됨에 따라이 위치에 대한 숫자 설명이 업데이트됩니다.

* getPose ()를 사용하여이 앵커의 현재 숫자 위치를 가져옵니다. 이 위치는 update ()가 호출 될 때마다 변경 될 수 있지만 자연스럽게 변경되지는 않습니다.

* mathematically(수학적으로) :
```
point_world = anchor.getPose (). 변형 점 (point_local);
point_world = anchor.getPose (). toMatrix () * point_local;
```

* anchor.getPose (). toMatrix (...)는이 앵커의 위치에서 객체를 렌더링 할 때 뷰 및 투영 행렬로 작성하기에 적합한 행렬을 제공합니다.

* 앵커는 해시 가능하며 예를 들어 HashMaps에서 키로 사용할 수 있습니다.

* 앵커는 ARCore에서 처리 오버 헤드가 발생합니다. 불필요한 앵커를 해제하려면 detach ()를 사용하십시오.



## [ArCoreApk](https://developers.google.com/ar/reference/java/com/google/ar/core/ArCoreApk)
> public class ArCoreApk

* 장치에서 ARCore의 상태를 관리하기 위한 정적 방법


## [AugmentedImage](https://developers.google.com/ar/reference/java/com/google/ar/core/AugmentedImage)
> public class AugmentedImage

* 현실 세계의 증강 이미지에 대한 현재의 최상의 지식을 설명합니다.

* ARCore는 포즈와 물리적 크기를 추정하기에 충분한 정보가 아직 없더라도 환경에서 이미지를 처음 감지하면 AugmentedImage를 반환합니다. 이 경우 AugmentedImage는 추적 상태를 일시 중지합니다.
* 데이터베이스에 선택적 물리적 크기를 지정하면 초기 포즈 및 물리적 크기 추정 프로세스의 속도가 향상됩니다.
* 전체 동작 추적 시스템 (예 : 프레임의 카메라 추적 상태가 추적 중)을 추적하는 경우에도 AugmentedImage는 추적 상태 PAUSED를 가질 수 있습니다.


## [AugmentedImageDatabase](https://developers.google.com/ar/reference/java/com/google/ar/core/AugmentedImageDatabase)
> public class AugmentedImageDatabase

* ARCore가 탐지하고 추적 할 이미지 목록이 포함 된 데이터베이스입니다.

* 이미지 데이터베이스는 최대 1000 개의 이미지를 지원합니다. 데이터베이스는 SDK에 제공된 arcoreimg 명령 줄 데이터베이스 생성 도구로 생성하거나 개별 이미지를 AugmentedImageDatabase에 추가하여 런타임에 동적으로 생성 할 수 있습니다.

* 한 이미지 데이터베이스만 세션에서 활성화 할 수 있습니다. TRACKING / PAUSED 상태인 현재 활성 이미지 데이터베이스의 이미지는 현재 또는 다른 이미지 데이터베이스가 현재 세션 Config에서 활성화 된 경우 즉시 STOPPED 상태로 설정됩니다.


## [Camera](https://developers.google.com/ar/reference/java/com/google/ar/core/Camera)
> public class Camera

* 이미지를 캡처하는 데 사용되는 카메라에 대한 정보를 제공합니다.
* 카메라는 오래 지속되는 객체이며 Session.update ()가 호출 될 때마다 Camera의 속성이 업데이트됩니다.


## [Config](https://developers.google.com/ar/reference/java/com/google/ar/core/Config)
> public class Config

* 세션을 구성하는 데 사용되는 설정을 보유합니다.


## [Frame](https://developers.google.com/ar/reference/java/com/google/ar/core/Frame)
> public class Frame

* update ()를 호출하여 AR 시스템의 상태와 변경 사항을 캡처합니다.


## [HitResult](https://developers.google.com/ar/reference/java/com/google/ar/core/HitResult)
> public class HitResult

* 광선과 추정된 실제 지오메트리 간의 교차를 정의합니다.


## [ImageMetadata](https://developers.google.com/ar/reference/java/com/google/ar/core/ImageMetadata)
> public class ImageMetadata

* 카메라 이미지 캡처 결과의 메타 데이터에 대한 액세스를 제공합니다.
* 개별 키에 대한 자세한 내용은 NDK 카메라 설명서에서 비슷하게 명명된 상수에 대한 참조 정보를 참조하십시오.


## [LightEstimate](https://developers.google.com/ar/reference/java/com/google/ar/core/LightEstimate)
> public class LightEstimate

* 실제 장면의 예상되는 조명에 대한 정보를 보유합니다.
* getLightEstimate ()에 의해 반환 됨


## [Plane](https://developers.google.com/ar/reference/java/com/google/ar/core/Plane)
> public class Plane

* 실제 평면 표면에 대한 현재의 최상의 지식을 설명합니다.

### Merging / Subsumption
* 둘 이상의 평면이 자동으로 단일 부모 평면으로 병합 될 수 있으므로 각 자식 평면의 getSubsumedBy()가 부모 평면을 반환합니다. 포함 된 평면은 부모 평면과 동일 해지며 독립적으로 추적 된 것처럼 동작합니다 (예 : getUpdatedTrackables (Class)의 출력에 포함됨).

* 평면은 해시 가능하며 예를 들어 HashMaps의 키로 사용될 수 있습니다. 소면 항공기는 부모님과 형제 자매와 별개입니다.

**Change from Developer Preview 1:** 두 개의 평면 객체가 시스템에서 감지 한 동일한 논리 평면을 참조 할 수 있습니다. 비교할 때는 항상 equals (Object)를 사용해야합니다.



## [Point](https://developers.google.com/ar/reference/java/com/google/ar/core/Point)
> public class Point

* ARCore가 추적중인 공간의 한 지점을 나타냅니다. 이러한 객체는 createAnchor(Pose) 또는 hitTest(float, float)가 포인트 클라우드에 대한 결과를 반환하는 경우의 부작용으로 만들어집니다.

* 참고 : 두점의 객체는 ARCore가 관리하는 동일한 논리 점을 참조 할 수 있습니다. 비교할 때는 항상 equals (Object)를 사용해야합니다.



## [PointCloud](https://developers.google.com/ar/reference/java/com/google/ar/core/PointCloud)
> public class PointCloud

* 관측된 3D 포인트와 자신의 값 집합을 포함합니다.



## [Pose](https://developers.google.com/ar/reference/java/com/google/ar/core/Pose)
> public class Pose

* 하나의 좌표 공간에서 다른 좌표 공간으로의 불변의 경질 변환을 나타낸다.
* 모든 ARCore API에서 제공되는 Poses는 항상 오브젝트의 로컬 좌표 공간에서 월드 좌표 공간으로의 변환을 설명합니다 (아래 참조).
* 즉, ARCore API의 Poses는 OpenGL 모델 행렬과 동일하다고 생각할 수 있습니다.
* 변환은 원점에 대한 쿼터니언 회전을 사용하여 변환을 정의합니다.
* 좌표계는 OpenGL 규칙처럼 올바르게 처리됩니다.
* 번역 단위는 미터입니다.

### World Coordinate Space
* 환경에 대한 ARCore의 이해가 변화함에 따라 일관성을 유지하기 위해 세계 모델을 조정합니다. 이런 일이 발생하면 카메라와 앵커의 숫자 위치 (좌표)가 크게 변경되어 자신이 나타내는 실제 위치의 적절한 상대 위치를 유지할 수 있습니다.
* 이러한 변경 사항은 모든 프레임이 완전히 고유 한 세계 좌표 공간으로 간주되어야 함을 의미합니다. 앵커와 카메라의 숫자 좌표는 검색되는 동안 렌더링 프레임 외부에서 사용되어서는 안됩니다. 위치를 단일 렌더링 프레임의 범위를 넘어서 고려해야 할 경우 앵커를 만들어야하거나 근처에있는 앵커와 관련된 위치를 사용해야합니다.



## [Session](https://developers.google.com/ar/reference/java/com/google/ar/core/Session)
> public class Session

* AR 시스템 상태를 관리하고 세션 수명주기를 처리합니다. 이 클래스는 ARCore API의 주요 진입 점입니다.
* 이 클래스를 사용하면 세션을 만들고, 구성하고, 시작/중지 할 수 있으며 가장 중요한 것은 **카메라 이미지 및 장치 포즈에 액세스 할 수있는 프레임을 수신** 할 수 있습니다.



## [Stub](https://developers.google.com/ar/reference/java/com/google/ar/core/Stub)
> public class Stub

* ARCore의 playstore 자동 업데이트를 위해 스텁 apk를 만드는 빈 클래스



## [Trackable](https://developers.google.com/ar/reference/java/com/google/ar/core/Trackable)
> public class Trackable


| Known Indirect Subclasses |
| :-: |
| AugmentedImage, Plane, Point |


* 추적 가능 항목은 ARCore가 추적하고 앵커를 연결할 수있는 항목입니다.



## [TrackingState](https://developers.google.com/ar/reference/java/com/google/ar/core/TrackingState)
> public class TrackingState

* 추적 가능 항목의 추적 상태를 설명합니다.

