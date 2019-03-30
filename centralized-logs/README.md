### centralized log 

#### 개요
- java application 여러 대의 서버에서 운영할 때 로그를 한 곳에 수집하는 방법에 대해 기술한다. 

#### 설치할 어플리케이션
- filebeat (java application 에 설치)
- logstash 
- elasticsearch 

#### 순서 
- filebeat.yml 
  - java application log 위치를 기록하고, multiline 적용 여부에 대한 옵션을 추가한다. 
  - filebeat->logstash, filebeat->elasticsearch 전송이 가능한데 logstash 에서 전송된 로그 필드를 변경하기 때문에 logstash로 전송한다. 
- logstash-pipeline.yml
  - logstash pipeline 을 활용하면 task 갯수를 늘리거나 줄일 수 있다. 
- filebeat-webserver.yml
  - logstash 의 beat input plugin을 사용하면 filebeat로부터 전송한 로그를 처리할 수 있다. 
  - beat->filter->elasticsearch 으로 전송하고, 이때 같이 전송된 filebeat meta 정보 기반으로 elasticsearch index 를 지정한다. 

