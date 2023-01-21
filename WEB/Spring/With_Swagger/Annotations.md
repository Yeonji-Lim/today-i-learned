# @ApiOperation

해당 api 설명 작성

# @ApiModelProperty

DTO 예제 설명에 쓰인다.

```
@ApiModelProperty(example="그룹 idx")  
private Long clubIdx;  
  
@ApiModelProperty(example="그룹 이름")  
private String name;  
  
@ApiModelProperty(example="그룹 소개")  
private String content;  
  
@ApiModelProperty(example="그룹 이미지 url")  
private String imgURL;  
  
@ApiModelProperty(example="그룹 모집 상태 (모집 중, 모집 완료)")  
private String recruitStatus;
```

![[swagger_response_description.png]]