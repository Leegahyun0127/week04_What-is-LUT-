# week04_assignment_B976143_leegahyun 
#### 1. What is LUT?
#### 2. What is Logsapce and main difference with sRGB, why and when we use?

## 1.What is LUT? 
### =(Look-Up Table) 룩업 테이블 
Look-Up Table(LUT)는 색상hue, 채도saturation, 조도brightness를 "수학적으로 정확하게" 조정하여 촬영된 원본 이미지의 RGB값을 새로운 RGB값으로 만들어주는 방법이다.
LUT는 과학적으로 정밀하게 쓰일 수도 있고(예를 들면, sRGB색공간을 DCI P3색공간으로 옮기기 위해) 또는 어떤 특정한 룩look을 구현하기 위해 사용할 수도 있다

LUT (known as Lookup Table), is a term used to describe a predetermined array of numbers that provide a shortcut for a specific computation. 
In the context of color grading, a LUT transforms color input values (camera) to your desired output values (final footage)

the LUT is the means to make up the difference between source and result.((All cases assume the colorist (or you) is grading through a correctly calibrated monitor for evaluation and finishing. LUTs in no way replace proper calibration or color correction.
The color space and input level was intended to be for that particular LUT, and the type of shot it was intended for.

![df](https://s.studiobinder.com/wp-content/uploads/2019/02/What-is-LUT-LUT-Color-Grading-Ridley-Scott-Film-LUTs-Pack.jpg)

#### Why use LUTs on footage?
1. Set a predetermined look for a specific visual feeling
2. Increase the speed at which you can color grade
3. Use as a reference point to develop your unique style
4. They can also make log or flat footage come to life by adding contrast and style or converting it back into a Rec.709 colour space.
You can even load a LUT into a monitor or display to calibrate it to get an idea of what the finished look of your film might be.

Now, there are several different types of LUTs available: calibration, transform, viewing, 1D and 3D


## 1D LUTs vs. 3D LUTs
There are generally two types of LUTs out there that you can use. Both types will use both bit size and bit depth to determine the accuracy
of your lookup table.

### 1D LUT 
1D LUT is called such because it is controlled by one value setting, and can be boiled down to a gamma curve preset. While this achieves the general goal of a LUT, it does not provide you with the level of control most editors and colorists would prefer. You will most commonly find 1D LUTs that use the .lut extension.
1D LUT, 말 그대로 1차원 LUT는 보정하고자 하는 값에 1:1로 대응하는 그래프이며 우린 이를 포토샵과 프리미어 등에서 흔히 접할 수 있는 'Curve' 플러그인을 통해 확인할 수 있으며, 이 1차원적 좌표를 여기저기 뒤틀어서 색 정보에 변경을 주는 것이라 보면 된다.

![fd](https://file.bodnara.co.kr/webedit/hardward/guide/lut/curve.jpg)

### 3D LUT
A 3D LUT maps hue, saturation, and brightness to an individual axis, so that you have much more control over specific color values in your image. These are commonly found with .cube file extensions.
3D LUT는 Red, Green, Blue 로 이루어진 3축의 입체 좌표계를 만들어 이용하는 방법으로 일상생활에서 흔히 접할 수 있는 모든 색을 이 3D LUT 안의 특정 좌표에 위치시킬 수 있다.
이렇게 해서 생성된 하나의 입체 큐브를 쉽게 말해 '색 공간' 이라 볼 수 있겠다.이 큐브 또한 마찬가지로 뒤틀거나 뒤집거나 하는 등의 변경을 주어서 색을 보정, 혹은 변경이 가능하며, 1DLUT와 다르게 휘도, 채도, 색상등을 한 번에 변경할 수 있다.

![d](https://file.bodnara.co.kr/webedit/hardward/guide/lut/lut.jpg)


#### Where should we use LUTS ?
So, where should you use LUTs? LUTs can be used in any programme that has the ability to grade your footage. 
The most popular are Adobe Premiere Pro, Blackmagic DaVinci Resolve and Final Cut. You can even load a LUT into Photoshop to apply it to a still image.
As LUTs are so universal they are a better option when moving between software, instead of saving presets within that programme. By using LUTs you can do quick overall corrections, make certain colours ‘pop’ or add cinematic style, all depending on the values that are contained within that LUT.

#### 다양한 LUT의 종류 
##### 1.Technical LUTs
테크니컬 LUT는 이미지를 하나의 색공간(color space 또는 gamut)에서 다른 색공간으로 옮기기 위해 만들어졌다.  해당 LUT의 최종 목표는 두 가지 다른 시청 환경에서 똑같은 결과물을 만들어내는 것이다. 예를 들면, (똑같은 소스를) TV에서 보는 것과 잉크젯 프린터로 출력해서 보는 결과를 똑같이 맞춰주는 것이다.

##### 2.Creative LUTs:
크리에이티브 LUT는 다른 소프트웨어에서도(예를 들면, 프리미어 프로와 다빈치 등에서) 늘 한결같이 LUT가 가진 하나의 룩look을 표현할 수 있게 해준다.

##### 3.Camera LUTs
카메라 LUT의 좋은 예가 ARRI Alexa의 Rec709 LUT다.  이 LUT는 ARRI의 flat한 LOG-C에 적용하기 위해 디자인 되어 있다.  이런 종류의 LUT는 technical LUT와 creative LUT를 합친 결과물이라고 할 수 있다.  camera LUT는 왠지 수학적으로 정밀하게 만들어졌을 것만 같다.  그러니 해당 LUT를 사용할 때마다 정확하게 작동하리라 기대하게 된다.  그렇지만 사실은 그렇지 않다.바로 노출exposure 때문이다.
(장면마다) 카메라의 센서에 도달하는 광량이 다르기 때문에 암부와 명부의 관계가 바뀐다.  그러면 해당 이미지에 적용한 LUT도 영향을 받는다. 결과적으로 camera lut는 creative 툴이고 (그레이딩을 하기 위한) 특정한 목표를 가지고 만들어졌다.  그러나 해당 카메라로 촬영한 모든 화면에 일괄적으로 적용할 수는 없다.
