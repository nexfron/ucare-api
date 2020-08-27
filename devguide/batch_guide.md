# 배치 개발 가이드


### 배치 관련 소스

| 구분 | 경로 |
|:---:|:---:|
| `xml` | resources\spring\context-scheduling.xml|
| `java` | com\nexfron\core\batch |


### 배치 관련 설정 및 변경
*(예시 : 상담유형별 통계 배치 테이블)*

 - `java` 파일 생성 및 로직 작성 
   * `BatchConslTypeStatisticsService.java` 실행 함수 선언
      ```java
      public interface BatchConslTypeStatisticsService extends UcareBaseService<BatchConslTypeStatisticsPVO, BatchConslTypeStatisticsDVO> {
        public void insertConslTypeData();
      }
      ```
      
   * `BatchConslTypeStatisticsServiceImpl.java` 비즈니스 로직 작성
      ```java
      ...

      @PostConstruct // init method는 WAS가 띄워질 때 실행 
	  private void init() {
        // 기존 데이터 삭제
        this.batchConslTypeStatisticsDAO.deleteDataNoAOP("batchConslTypeStatistics.deleteConslTypeStatistics", new BatchConslTypeStatisticsDVO());
        
        // 당일 상담이력 데이터를 집계 테이블에 INSERT
        int rslt = this.batchConslTypeStatisticsDAO.insertDataNoAOP("batchConslTypeStatistics.insertConslTypeStatistics", new BatchConslTypeStatisticsDVO());
	  }
	
      @Override
      @Async
      public void insertConslTypeData() {
        this.init();
      }

      ...
      ```


 - `context-scheduling.xml` 파일 변경
    * 수행될 작업 설정
    ```xml
     <bean id="batchConslTypeStatisticsJob" class="org.springframework.scheduling.quartz.MethodInvokingJobDetailFactoryBean">
		<property name="targetObject" ref="batchConslTypeStatisticsService" />
		<property name="targetMethod" value="insertConslTypeData" />
		<property name="concurrent" value="false" />
	</bean>
    ```

      * 작업 수행을 얼마 간격으로 할 것인지 설정

        [참고] cron 표현식 작성법 https://zamezzz.tistory.com/197
        
    ```xml
    <bean id="batchConslTypeStatisticsTrigger" class="org.springframework.scheduling.quartz.CronTriggerFactoryBean">
		<property name="jobDetail" ref="batchConslTypeStatisticsJob" />
		<property name="cronExpression" value="0 0 0/1 1/1 * ? *" /> <!-- 1시간마다 수행 -->
	</bean>
    ```

    * 위에 설정한 내용이 실제 수행되도록 세팅
    ```xml
     <bean id="scheduler" class="org.springframework.scheduling.quartz.SchedulerFactoryBean">
		<property name="triggers">
			<list>
				<ref bean="batchConslTypeStatisticsTrigger" />
			</list>
		</property>
	</bean>
    ```




