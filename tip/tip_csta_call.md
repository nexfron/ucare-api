# CSTA

CSTA(Computer Supported Telecommunication Application) 
  - 유럽의 표준화 기관인 ECMA(European Computer Manufacturer's Association) 에 의해 작성된 PBX-컴퓨터간 인터페이스 표준
  - CTI 표준을 위한 위한 서비스와 응용계층 프로토콕의 표준안 [ECMA-269](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-269.pdf)



## 참고
  - [NXCAPI API 소프트폰 개발 가이드](https://slidesplayer.org/slide/11047194/)


## Connection State Model
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/24-Figure5-1.png)

  - Null : Call 과 Device 사이에 어떠한 관계도 없는 상태
  - Initiated : Device 가 서비스를 요구하는 상태로 이때 Call을 생성한다(Dialing 상태라고함)
  - Alerting : Device의 링이 울리고 있는 상태
  - Connected : Device가 Call에 참여하여 다른 Device와 통신하는 상태
  - Held : Connected 상태의 Call 이 비 활성화된 상태, 논리적으로는 Call에 참여하고 있지만 물리적으로 참여하고 있지 않은 상태
  - Queued : 정상적인 상태의 Call이 그 다음 상태로 천이하기 위하여 대기하고 있는 상태
  - Failed : 정상적인 상태의 진행이 중지된 상태 



# Call Service

## 1Alternate Call 
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/34-Figure8-1.png)

## 2.Answer Call 
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/35-Figure9-1.png)

## 3.Associate Data

## 4.Call Completion 

## 5.Clear Call
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/36-Figure10-1.png)

## 6.Clear Connection
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/37-Figure11-1.png)

## 7.Conference Call Service 
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/38-Figure12-1.png)

## 8.Consultation Call Service 

## 9.Divert Call Service
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/40-Figure14-1.png)

## 10.Hold Call Service
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/41-Figure15-1.png)

## 11.Make Call
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/42-Figure16-1.png)

## 12.Make Predictive Call Service 
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/43-Figure17-1.png)

## 13.Park Call Service

## 14.Query Device Service 

## 15.Reconnect Call Service 
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/46-Figure18-1.png)

## 16.Retrieve Call Service
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/47-Figure19-1.png)

## 19.Single Step Conference Service

## 20.Single Step Transfer Call Service 

## 21.Transfer Call Service 
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/49-Figure20-1.png)





# Call Event

## Service Initiated

[Service Initiated - ECMA 269](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-269.pdf#page=424&zoom=100,41,152)

originated
networkReached
## delivered
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/55-Figure24-1.png)

established
failed
## diverted
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/56-Figure25-1.png)

queued
## connectionCleared
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/55-Figure23-1.png)

held
## retrieved
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/61-Figure32-1.png)

## transferred
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/62-Figure34-1.png)

## conferenced
![](https://d3i71xaburhd42.cloudfront.net/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/54-Figure22-1.png)


## 참조
  - [CSTA Services](http://neowizard.tistory.com/attachment/cfile9.uf@196196254B13B90C452B82.pdf)
  - [A brief history-Call 이미지 참조](https://www.semanticscholar.org/paper/A-brief-history.-Moran/9ea68d848c651b9bc2b0f7d8c1c896f7ce93194a/figure/0)