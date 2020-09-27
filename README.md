# week04_assignment_B976143_leegahyun 
#### 0. Colorspace
#### 1. What is LUT?
#### 2. What is Logsapce and main difference with sRGB, why and when we use?

## 0.Colorspace, gamma
### Color space
색 공간(色空間, color space)은 색 표시계(color system)를 3차원으로 표현한 공간 개념이다. 색 표시계의 모든 색들은 이 색 공간에서 3차원 좌표로 나타낸다.
아주 기본적인 color space 에 대한 정의인 두가지, CIE 1931 RGB color space, CIE 1931 XYZ color space 가 있다
여기서 색 표시계(color system)란 CIERGB, CIEXYZ, CIELAB, CIELUV 등의 색 체계를 말한다. 
특히, 색 디자인이나 디지털 색 처리에 기본적으로 사용되고 있는 색 공간인 CIELAB 색 공간은 먼셀 색 표시계의 기본 원리인 색의 3속성(색상, 명도, 채도)을 살림과 동시에 CIEXYZ 색 표시계의 불균등한 색 공간을 개선하기 위하여 개발된 것이다. 이 색 공간은 색상(hue), 명도(lightness), 채도(chroma)를 3차원 공간의 각각의 기본 축으로 하는 공간이다. 

![ㄹㅇㅁㅇㄴ](https://upload.wikimedia.org/wikipedia/commons/3/3b/CIE1931xy_blank.svg)CIE 1931 Colorspace


CIE xy chromaticity diagram 에서 밑의 직선을 제외한 말발굽 모양의 숫자가 표시된 부분을 spetral locus 라고 부르는데, 이는 파장의 길이에 따라 달라지는 가시광선을 나타낸다. 곡선에 표시된 숫자는 파장의 크기를 나타낸다. 아래 직선은 line of purple 이라고 하는데, 여기서 재미있는 것은 spectral locus 와 white point 사이에 있는, 즉 환경에 정해진 흰색 사이에 있는 색은 얼마든지 하나의 파장을 가진 빛으로 나타낼 수 있고, 그게 아닌 line of purple 과 white point 사이에 있는 색은 하나의 파장을 가진 빛으로 나타낼 수 없다.

CIE XYZ 는 다른 color space 와 변환으로 연결되어있는 이론상으로 기본적인 color space 이다. CIE XYZ 에서 파생된 여러가지 color space 들이 존재하는데 몇가지만 살펴보겠다. 첫번째는 CIE LAB 이라는 color space 인데 이는 사람이 인지할 수 있는 색의 변화에 맞게 개선되었으며, 프린터가 주로 사용하는 CMYK Color Model, 디스플레이에서 주로 사용되는 RGB Color Model 둘다 포함한다고 한다. 두번째는 CIE LUV 로, 주로 빛으로 색을 나타내는 컴퓨터 그래픽에서 사용되고, 이 또한 perceptual uniformity 를 개선하였다고 한다. 이 외에도 꽤 많은 color space 들이 존재한다.

색의 3속성인 색상(hue), 명도(lightness), 채도(chroma)를 3차원 공간의 각각의 축으로 형성된 색 공간은 컬러 디자인이나 컬러 공학 등의 학문 또는 산업분야에서 컬러를 다루는 데 있어서 기본적으로 이해하여야 할 개념이다.

빨강, 노랑, 초록, 파랑, 보라 등으로 구분되는 색을 나타내는 색상(hue)은 색 공간을 지구로 비유할 경우 적도 상에서 경도 즉, 색상각(hue angle)으로 표현, 0도~360도의 범위를 가지며, 시계 방향으로 변화된다. 또한 이 색 공간은 대응색(opponent color) 관계를 쉽게 나타낸다. 대응색 관계란 명도 축을 기준으로 대칭의 위치에 있는 두 색의 관계를 말하며 서로 보색 관계에 있을 나타낸다.
모든 색들의 밝고 어둠을 나타내는 명도(lightness)는 색 공간을 지구로 비유할 경우 남극과 북극을 연결하는 축으로서 남극을 검은색, 북극을 흰색으로 하며 그 사이에는 회색들로 배열된다.
모든 색들의 깨끗한 정도를 나타내는 채도(chroma, saturation)는 색 공간의 명도축을 0으로 하고 적도에 가까이 갈수록 커진다.

색 공간의 중요한 용도 가운데 하나는 색차 계산(color difference)이다. 이는 색 공간에 존재하는 두 점 즉, 두 색들 사이의 거리를 계산하여 공학적으로 활용한다. 예를 들면 컬러 영상 분할(color image segmentation)은 CIELAB 색 공간에서 색차 계산 결과를 이용하여 CIELAB 색 공간에서 영상 분할이 이루어져야 한다. 그러나 간혹 컬러 영상 분할에 관한 연구 논문들 중에는 RGB 데이터를 바탕으로 색차 계산한 결과를 가지고 RGB 데이터로 영상분할을 한 논문들이 발견되곤 하는데 이는 치명적인 오류에 해당된다. 왜냐하면 컬러 영상 장비에서 다루는 RGB는 시각의 RGB가 아니고 단지 코드에 불과할 뿐 아니라 균등색 공간(uniform color space)도 아니기 때문에 공학적인 계산은 의미가 없을 뿐만 아니라 부정확하기 때문이다.

### 자주 쓰이는 색공간 
#### 1. RGB 색 공간
RGB 색 공간은 색을 혼합하면 명도가 올라가는 가산 혼합 방식으로 색을 표현한다. RGB 가산혼합의 삼원색은 빨강(Red), 녹색(Green)[1], 파랑(Blue)을 뜻한다. RGBA은 RGB와 동일하며, 알파(Alpha)라는 투과도를 덧붙인 것이다. RGB 색 공간은 삼원색에 해당하는 세 가지 채널의 밝기를 기준으로 색을 지정한다. RGB 색 공간은 웹 색상 표현의 기본 원리이다
![ㅏㅛㅑ](https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/RGBCube_b.svg/400px-RGBCube_b.svg.png)

#### 2. CMYK 색 공간
CMYK 색 공간은 인쇄과정에서 쓰이는 감산 혼합 방식으로, 흰 바탕에 네 가지 잉크의 조합으로 색을 나타내는 것을 말한다. 색을 혼합하면 명도가 낮아지기에 감산 혼합이라고 한다. CMYK는 인쇄에 쓰이는 4가지 색은 옥색(Cyan), 자홍색(Magenta), 노랑(Yellow), 검정(Black)을 뜻한다.
![ㄹㅁㅇㄴ](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Synthese-.svg/400px-Synthese-.svg.png)

#### 3. HSV 색 공간
HSV 색 공간은 색상(Hue), 채도(Saturation), 명도(value)를 기준으로 색을 구성하는 방식이다. 감산 혼합이나 가산 혼합보다 색상의 지정이 직관적[2]이기 때문에 시각 예술에서 자주 쓰인다.

![ㄹㅇㄴ](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/HSV_cone.jpg/400px-HSV_cone.jpg)
#### 4. CIE 색 공간
CIE는 국제 조명 위원회(프랑스어: Commission internationale de l'éclairage)를 프랑스어식으로 표기한 준말이며, CIE 색 공간이란 컬러 매칭 실험을 통하여 생성된 R, G, B 데이터를 바탕으로 만들어진 CIEXYZ 색 공간과 CIELAB 색 공간, 그리고 CIELUV 색 공간이 대표적인 색 공간이다.

여기서 CIEXYZ 색 공간은 '균등 색 공간'이 아니어서, 이를 수식적으로 변환하여 만들어진 것이 CIELAB 색 공간과 CIELUV 색 공간이며, 이 두 색 공간은 색차를 계산할 때 비교적 정확한 계산이 이루어진다.

여기서 '균등 색 공간'이란 '불균등 색 공간'의 대립 개념이며, 불균등 공간에서는 색상들을 나타내는 선, 채도들을 나타내는 선들이 일정하지 않고 불규칙하게 배열되기 때문에 색 공간에서 두 점의 거리 즉, 색의 차이를 계산하면 정확하지 않다.

## Gamma
감마 보정(감마 교정)은 비디오 카메라, 컴퓨터 그래픽 등에서 비선형 전달 함수(nonlinear transfer function)를 사용하여 빛의 강도(intensity) 신호를 비선형적으로 변형하는 것을 말한다. 일반적으로 감마 보정(gamma correction)이란 용어가 널리 쓰이나, 대부분의 경우 감마 부호화(gamma encoding)란 표현이 더 적절하다
### 감마 보정의 목적 
인간의 시각은 베버의 법칙(Weber's law)에 따라 밝기에 대해 비선형적으로 반응한다. (청각과 같은 다른 감각들도 자극에 대해 비선형적으로 반응한다.) 이 때문에 예를 들어 채널 당 8 bit와 같이 한정된 정보표현량(bit depth)안에서 선형적으로 빛의 밝기를 기록하면, 사람의 눈이 민감하게 반응하는 어두운 부분의 경우 밝기가 변할때 부드럽게 느껴지지 않고 단절되어 보이는 현상(posterization)이 발생한다. 따라서, 주어진 정보표현량의 한계 안에서 최적의 화질을 보여주기 위해선 비선형적으로 부호화하여 어두운 부분을 더 자세히 기록할 필요가 있다

### Linear workflow
실제 세상의 빛은 linear로 작용, 우리가 보는 빛의 양은 광원들의 빛의 양을 합친 값이다. 즉, 실제 세상에서는 input이 output과 일정, 동등하다. 이를 linear라고 한다.
모니터들이 가장 많이 사용하는 color space는 sRGB(non-linear, 8bit, gamma 2.2) 안에서 이뤄진다. sRGB안에서는 gamma correction이라는 것이 작용하는데, 이는 우리가 본 luminance값을 비디오나 사진에서 암호화, 해독하던 방식을 말한다.
그래서 이를 다시 linear로 바로잡기 위해 의도적으로 수치값을 대입한다. 이 수치를 gamma라고 한다.
![fa](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkI5tJ%2FbtqtYLHZ3Gs%2Fet3rchG3M94RLRGvnd0Mek%2Fimg.jpg)


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
 카메라 LUT은 카메라 제조사에서 직접 만들어 제공하는 LUT이다. 카메라 LUT의 좋은 예가 ARRI Alexa의 Rec709 LUT다.이 LUT는 ARRI의 flat한 LOG-C에 적용하기 위해 디자인 되어 있다.  이런 종류의 LUT는 technical LUT와 creative LUT를 합친 결과물이라고 할 수 있다.  camera LUT는 왠지 수학적으로 정밀하게 만들어졌을 것만 같다.  그러니 해당 LUT를 사용할 때마다 정확하게 작동하리라 기대하게 된다.  그렇지만 사실은 그렇지 않다.바로 노출exposure 때문이다.

(장면마다) 카메라의 센서에 도달하는 광량이 다르기 때문에 암부와 명부의 관계가 바뀐다.  그러면 해당 이미지에 적용한 LUT도 영향을 받는다. 결과적으로 camera lut는 creative 툴이고 (그레이딩을 하기 위한) 특정한 목표를 가지고 만들어졌다.  그러나 해당 카메라로 촬영한 모든 화면에 일괄적으로 적용할 수는 없다.


## What is Logspace?
로그 간격의 벡터(Logarithmically Spaced Vector) 생성
The logspace function generates logarithmically spaced vectors. Especially useful for creating frequency vectors, it is a logarithmic equivalent of linspace and the ":" or colon operator.

### Log space color
The Log (logarithmic) color space has been around for quite a while. Initially high-end post houses used it with scanned film negatives in a color space called Cineon Log. Now, pretty much all camera manufacturers offer their own Log curve (or multiple). There is S-Log 2&3 (Sony), LogC (Arri), Canon Log, V-Log (panasonic), Red Logfilm, Blackmagic Log, etc. Each of them are different, usually tailored for the color science of the particular manufacturer’s products.


### Log vs. Linear Color Space _ 
![d](https://assets.rocketstock.com/uploads/2017/05/Log-Curve.jpg)
Above is a (not necessarily exact) representation of the differences between a linear color curve and a Log color curve. If you’re familiar with  curves, you know that the bottom left of the curve represents your blacks and shadows, and as you move to the top right of the curve, you have your highlights and whites. As you can see, a Log curve pushes the darker part of the image upwards to retain shadows. The top of the curve shifts down to retain highlights. Therefore, you retain more data from each side of the color curve.

### What is sRGB?
sRGB is pretty much the default color space everywhere you look. This means that most browsers, applications, and devices are designed to work with sRGB, and assume that images are in the sRGB color space. In fact, most browser simply ignore the embedded color space information in images and render them as sRGB images
![dfad](https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Cie_Chart_with_sRGB_gamut_by_spigget.png/500px-Cie_Chart_with_sRGB_gamut_by_spigget.png)

#### pros
- Displayed consistently across all programs
- Simplifies workflow
- Suitable for normal prints
- Most people can’t tell the difference anyway

### sRGB_ Which to use?
First of all, if you publish your images on the web, you should always save and publish them as sRGB. This is because most browsers will render images as sRGB regardless of what you save it as, causing Adobe RGB images to appear desaturated and washed out (the problem I was experiencing). Thus, if you want your images to look the same regardless of where it’s being displayed, you should always publish them as sRGB. This makes it so what you see when you save is what you get when it’s displayed

### Difference between sRGB and Logspace
In a linear color-space, the relationship between the stored numbers and the values they represent is a linear 1:1 ratio. This means that, for example, if you double the number, you double the intensity. That sounds really easy, but the problem is that the human eye sensitivity to light is much finer at lower intensities than at high intensities. In particular, if we're using 8 bits to represent values (which means a total of 256 shades), we'll end up with too many light shades, and not enough dark shades 

![dafsd](https://cdnb.artstation.com/p/media_assets/images/images/000/394/819/medium/image00.jpg?1552184196)

Thus, while a linear space makes perfect sense to use for computer processing, it is not suitable for human viewing because our eyes expect to see about the same amount of brightness change in between equal intervals. For example, our brain expects to see shade 32 twice as bright as 16, and shade 48 (which equals 32+16) twice as bright as 32.
To address this problem, most modern monitors apply a transformation called sRGB, a standard which uses a gamma curve to make the colors non-linear (figure 2). The curve is shallower at the bottom, so it can display more dark values, and steeper at the top, so it can have fewer light v

![fdasf](https://cdna.artstation.com/p/media_assets/images/images/000/394/820/medium/image02.jpg?1552184260) 
So now that we’ve briefly seen what linear and sRGB stand for, we are facing the following issue: we want our images to be processed in a linear space - which is computer friendly, but stored in sRGB - which is human friendly; However, since we’ve already established that 8bit linear doesn’t have enough dark shades, this could cause problems when converting to and from linear. As such, the solution we found was to widen the range from 8 to 16/32 bits, thus having much more dark shades to work with. These kind of images are called HDR (high dynamic range) and are typically stored as 32bit OpenEXR 

#### Log (short for logarithmic)
You can think of log as a color space “archiver” (in the same way zip or rar does it for files). This is because, while linear space increments values in equal steps, a logarithmic color space compresses the values in the white and black areas of an image, thus minimizing the space required to store the information (figure 4).
![dsa](https://cdnb.artstation.com/p/media_assets/images/images/000/394/821/medium/image01.jpg?1552184324)
As a side effect, this format also allows us to paint in more manageable formats such as 16 bit .tif; This is because, if you follow the above analogy, a 16 bit log file can “unarchive” to a 32bit linear format without clipping.
The most common log formats that you will encounter are ARRI Log and Cineon Dpx.















