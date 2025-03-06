# 유통 판매량 예측 및 재고 최적화

<div align="center">
  <h3><i>"시계열 데이터 기반 판매량 예측 및 재고 최적화"</i></h3>
  
  ![GitHub stars](https://img.shields.io/github/stars/username/retail-inventory-optimization?style=social)
  ![GitHub forks](https://img.shields.io/github/forks/username/retail-inventory-optimization?style=social)
  ![GitHub issues](https://img.shields.io/github/issues/username/retail-inventory-optimization)
  ![GitHub license](https://img.shields.io/github/license/username/retail-inventory-optimization)
</div>

## 📋 프로젝트 개요

본 프로젝트는 유통 매장의 상품별 판매량을 예측하고 이를 기반으로 재고를 최적화하는 모델을 개발하는 것을 목표로 합니다. 효율적인 재고 관리는 과재고로 인한 자금 묶임과 재고 부족으로 인한 기회 손실을 방지하여 매장 운영의 효율성을 높이는 데 핵심적입니다.

### 🎯 문제 정의

```
❓ 유통 매장에서 핵심 상품에 대한 수요량을 예측하고 재고를 최적화할 수 있는가?
```

### 재고 최적화가 중요한 이유:
- 🔹 과재고 시 자금이 묶여 유동성 문제 발생
- 🔹 재고 부족 시 판매 기회 손실
- 🔹 리드타임을 고려한 정확한 발주 계획 필요
- 🔹 상품별 특성에 맞는 맞춤형 재고 관리 필요

## 📊 분석 대상 상품

<div align="center">
  <table>
    <tr>
      <th>Product_ID</th>
      <th>Product_Code</th>
      <th>SubCategory</th>
      <th>Category</th>
      <th>LeadTime</th>
      <th>Price</th>
    </tr>
    <tr>
      <td>3</td>
      <td>DB001</td>
      <td>Beverage</td>
      <td>Drink</td>
      <td>2</td>
      <td>8</td>
    </tr>
    <tr>
      <td>12</td>
      <td>GA001</td>
      <td>Milk</td>
      <td>Food</td>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <td>42</td>
      <td>FM001</td>
      <td>Agricultural products</td>
      <td>Grocery</td>
      <td>3</td>
      <td>5</td>
    </tr>
  </table>
</div>

## 💻 기술 스택

<div align="center">
  <table>
    <tr>
      <th colspan="2" align="center">분류</th>
      <th align="center">기술</th>
      <th align="center">용도</th>
    </tr>
    <tr>
      <td rowspan="3" width="10%">💻</td>
      <td width="20%"><b>언어</b></td>
      <td width="25%">Python</td>
      <td width="45%">전체 프로젝트 개발</td>
    </tr>
    <tr>
      <td><b>데이터 처리</b></td>
      <td>Pandas, NumPy</td>
      <td>데이터프레임 조작 및 전처리</td>
    </tr>
    <tr>
      <td><b>시각화</b></td>
      <td>Matplotlib, Seaborn, Plotly</td>
      <td>데이터 시각화 및 결과 표현</td>
    </tr>
    <tr>
      <td rowspan="3">🤖</td>
      <td rowspan="2"><b>모델링</b></td>
      <td>TensorFlow, Keras</td>
      <td>딥러닝 모델 구현 및 학습</td>
    </tr>
    <tr>
      <td>Scikit-learn</td>
      <td>데이터 전처리, 모델 평가</td>
    </tr>
    <tr>
      <td><b>시계열 분석</b></td>
      <td>Statsmodels</td>
      <td>시계열 데이터 분해 및 분석</td>
    </tr>
  </table>
</div>

## 📈 데이터 탐색 및 인사이트

### 1️⃣ Product 3 (Beverage) 판매 패턴 분석

<div align="center">
  <img src="https://github.com/user-attachments/assets/363e3f28-1008-4e2e-905c-656e80a1e064" alt="Beverage 시계열 분석" width="700">
  <p><small>음료 판매량 추세 - 주중보다 주말에 판매량이 증가하는 패턴이 반복적으로 관찰됨</small></p>
</div>

#### 주요 인사이트:
- **요일별 판매 패턴**: 주말(토요일, 일요일)에 판매량이 크게 증가하는 뚜렷한 패턴
- **평일 중에는** 월요일, 수요일, 금요일에 비교적 높은 판매량
- **휘발유 가격과의 관계**: 특별한 상관관계 없음
- **장기 추세**: 전체 기간 기준으로 판매량 점진적 증가
- **계절성**: 월별/계절별 변동보다 요일별 변동이 더 지배적

<div align="center">
  <img src="https://github.com/user-attachments/assets/a90481ab-e734-400c-a496-816b0ab7808e" alt="Beverage 요일별 분석" width="600">
  <p><small>요일별 판매량 평균 - 주말(토요일, 일요일)에 판매량 증가</small></p>
</div>

### 2️⃣ Product 12 (Milk) 판매 패턴 분석

<div align="center">
  <img src="https://github.com/user-attachments/assets/dd7d1d7a-5705-466d-a96c-8f857bcc3833" alt="Milk 시계열 분석" width="700">
  <p><small>우유 판매량 추세 - 12월 판매량 상승</small></p>
  
  <img src="https://github.com/user-attachments/assets/ee96cae7-deab-4294-bcbe-10d8e3900f67" alt="Milk 시계열 분석" width="700">
  <p><small>우유 판매량 추세 - 주말 증가 패턴</small></p>
</div>

#### 주요 인사이트:
- **월별 판매 패턴**: 12월에 전체적인 판매량 증가, 특히 12월 중순에 피크
- **방문자 수와의 상관관계**: 방문자 수 증가에 따라 판매량도 비례적으로 증가 (상관계수 높음)
- **주말 효과**: 주말에 평일보다 판매량 증가
- **카테고리 내 위치**: Food 카테고리 내에서 가장 높은 판매량 기록
- **장기 추세**: 전체 기간 동안 약간의 감소 추세

<div align="center">
  <img src="https://github.com/user-attachments/assets/1a1190c0-ea8c-4b00-9f30-51fe17f99db2" alt="Milk 고객수 상관관계" width="600">
  <p><small>방문 고객 수와 우유 판매량의 추이</small></p>
  
  <img src="https://github.com/user-attachments/assets/0a64a03d-4719-4bb9-946f-2e48f59c0c88" alt="Milk 고객수 상관관계" width="600">
  <p><small>Customer Count and Milk Sales Quantity Correlation: 0.7123695976470086</small></p>
</div>

### 3️⃣ Product 42 (Agricultural products) 판매 패턴 분석

<div align="center">
  <img src="https://github.com/username/repository/blob/main/images/agri_time_series.png" alt="Agricultural products 시계열 분석" width="700">
  <p><small>농산물 판매량 추세 - 뚜렷한 계절적 패턴 관찰</small></p>
</div>

#### 주요 인사이트:
- **계절적 패턴**: 7월에 피크를 찍고 1월에 저점을 찍는 뚜렷한 계절적 패턴
- **연간 주기성**: 매년 유사한 패턴이 반복되는 안정적인 주기성
- **방문자 수와의 관계**: 방문자 수보다 계절적 요인이 더 큰 영향
- **휘발유 가격과의 상관관계**: 유의미한 상관관계 없음
- **예측 용이성**: 뚜렷한 계절적 패턴으로 인해 다른 상품보다 예측이 상대적으로 용이

<div align="center">
  <img src="https://github.com/user-attachments/assets/5b5c058a-d19c-4585-a498-c0e36d709" alt="농산물 시계열 분해" width="700">
  <p><small>시계열 분해 결과 - 관측값(observed), 추세(trend), 계절성(seasonal), 잔차(residual) 요소로 분리</small></p>
</div>

## 🧠 모델링 접근법

### 1️⃣ 데이터 전처리
- 시계열 특성 생성 (요일, 월, 연도, 휴일 여부 등)
- 이동 평균 및 지연 특성(lag features) 생성
- 데이터 정규화 및 스케일링
- 시계열 데이터셋 구성 (시퀀스 데이터 생성)

### 2️⃣ 모델 아키텍처
각 제품별로 최적화된 모델 구조 적용:

#### Product 3 (Beverage)
- **최종 선택 모델**: LSTM (Advanced)
  - 다중 LSTM 계층 (32 -> 16 -> 8)
  - Dropout 적용 (0.2)
  - Early Stopping 및 Adam 옵티마이저 사용

#### Product 12 (Milk)
- **최종 선택 모델**: LSTM (Advanced)
  - 다중 LSTM 계층 (64 -> 32 -> 16)
  - Dropout 적용 (0.2)
  - Early Stopping 및 Adam 옵티마이저(learning_rate=0.005) 사용

#### Product 42 (Agricultural products)
- **최종 선택 모델**: LSTM (Advanced)
  - 단일 LSTM 레이어(128 units)
  - Early Stopping 및 Model Checkpoint 적용
  - Adam 옵티마이저(learning_rate=0.0005) 사용

### 3️⃣ 모델 성능

#### Product 3 (Beverage) 모델 성능

<div align="center">
  <table>
    <tr>
      <td align="center" colspan="3">
        <h4>Baseline Model</h4>
        <img src="https://github.com/user-attachments/assets/7460e366-7dde-4064-b6b3-44738a08d72d" alt="Beverage Baseline 학습 곡선" width="500">
      </td>
      <td align="center" valign="middle" width="5%">➡️<br><small>하이퍼파라미터<br>튜닝</small></td>
      <td align="center" colspan="3">
        <h4>CNN Model</h4>
        <img src="https://github.com/user-attachments/assets/bdd4eb46-df0e-40c4-a325-a04fee348f38" alt="Beverage CNN 학습 곡선" width="500">
      </td>
    </tr>
    <tr>
      <td align="center"><b>MAE</b></td>
      <td align="center"><b>MAPE</b></td>
      <td align="center"><b>R²</b></td>
      <td></td>
      <td align="center"><b>MAE</b></td>
      <td align="center"><b>MAPE</b></td>
      <td align="center"><b>R²</b></td>
    </tr>
    <tr>
      <td align="center">2164.1002</td>
      <td align="center">0.1720</td>
      <td align="center">0.1426</td>
      <td></td>
      <td align="center">1810.8886</td>
      <td align="center">0.1564</td>
      <td align="center">0.6223</td>
    </tr>
    <tr>
      <td colspan="7" align="center"><h4>파라미터 및 특성 선택</h4></td>
    </tr>
    <tr>
      <td colspan="2">epoch=200</td>
      <td colspan="2">Dropout(0.2)</td>
      <td colspan="3">learning_rate=0.001</td>
    </tr>
    <tr>
      <td colspan="3">요일이 음료 판매 예측에 중요 요소</td>
      <td colspan="4">일주일 전 데이터로 예측 (요일별 변동 고려)</td>
    </tr>
    <tr>
      <td colspan="3">CustomerCount, Pre_order 변수 추가</td>
      <td colspan="4">WTI_Price 변수 추가, 요일 변수를 int형으로 변경</td>
    </tr>
  </table>
</div>

#### Product 12 (Milk) 모델 성능

<div align="center">
  <table>
    <tr>
      <td align="center" colspan="3">
        <h4>Baseline Model</h4>
        <img src="https://github.com/user-attachments/assets/d47fd744-c457-4633-95e5-5b261f925047" alt="Milk Baseline 학습 곡선" width="500">
      </td>
      <td align="center" valign="middle" width="5%">➡️<br><small>하이퍼파라미터<br>튜닝</small></td>
      <td align="center" colspan="3">
        <h4>LSTM Model</h4>
        <img src="https://github.com/user-attachments/assets/aefcf645-e646-4d1a-8860-daf03af282eb" alt="Milk LSTM 학습 곡선" width="500">
      </td>
    </tr>
    <tr>
      <td align="center"><b>MAE</b></td>
      <td align="center"><b>MAPE</b></td>
      <td align="center"><b>R²</b></td>
      <td></td>
      <td align="center"><b>MAE</b></td>
      <td align="center"><b>MAPE</b></td>
      <td align="center"><b>R²</b></td>
    </tr>
    <tr>
      <td align="center">2857.6650</td>
      <td align="center">0.2139</td>
      <td align="center">-0.4383</td>
      <td></td>
      <td align="center">2092.8562</td>
      <td align="center">0.1818</td>
      <td align="center">0.3686</td>
    </tr>
    <tr>
      <td colspan="7" align="center"><h4>파라미터 및 특성 선택</h4></td>
    </tr>
    <tr>
      <td colspan="2">epoch=100</td>
      <td colspan="2">LSTM(64,32,16), Dense(8)</td>
      <td colspan="3">Dropout(0.2)</td>
    </tr>
    <tr>
      <td colspan="3">방문고객 수가 예측에 중요 요소</td>
      <td colspan="4">판매수량, 가격, 리드타임 정보 통합</td>
    </tr>
    <tr>
      <td colspan="2">매장/유가/방문객 정보 추가</td>
      <td colspan="2">계절별 변수 추가</td>
      <td colspan="3">공휴일 변수 및 시차 변수 생성</td>
    </tr>
  </table>
</div>

#### Product 42 (Agricultural products) 모델 성능

<div align="center">
  <table>
    <tr>
      <td align="center" colspan="3">
        <h4>Baseline Model</h4>
        <img src="https://github.com/user-attachments/assets/fa8acb7c-cd40-4d28-b071-0a46dfe4de59" alt="Agricultural Baseline 학습 곡선" width="500">
      </td>
      <td align="center" valign="middle" width="5%">➡️<br><small>하이퍼파라미터<br>튜닝</small></td>
      <td align="center" colspan="3">
        <h4>LSTM Model</h4>
        <img src="https://github.com/user-attachments/assets/d1ddf23f-b675-405d-bd3b-2ff656d2c162" alt="Agricultural 튜닝 후 학습 곡선" width="500">
      </td>
    </tr>
    <tr>
      <td align="center" colspan="3"><b>MAE: 9.16</b></td>
      <td></td>
      <td align="center" colspan="3"><b>MAE: 8.37</b></td>
    </tr>
    <tr>
      <td colspan="7" align="center"><h4>특성 선택 및 모델링 전략</h4></td>
    </tr>
    <tr>
      <td colspan="3"><b>날짜적인 특징</b>: 공휴일 여부, 요일별 데이터</td>
      <td colspan="4"><b>외부적 특징</b>: 유가 데이터</td>
    </tr>
    <tr>
      <td colspan="3"><b>시계열 분해 특징</b>: Trend, Seasonal, Residual</td>
      <td colspan="4"><b>가격적인 특징</b>: Total Price = (Price * Qty)</td>
    </tr>
    <tr>
      <td colspan="2">판매량 평균 초과 달 정보</td>
      <td colspan="2">BaseColumn: Qty, CustomerCount</td>
      <td colspan="3">이틀 시차 변수 생성</td>
    </tr>
    <tr>
      <td colspan="3">고객 수 증가율 계산</td>
      <td colspan="4">IsOverQtyMonth 변수 추가</td>
    </tr>
  </table>
</div>

<div align="center">
  <h4>모델 성능 비교표</h4>
  <table>
    <tr>
      <th>모델</th>
      <th>설명</th>
      <th>MAE</th>
      <th>MAPE</th>
      <th>R² Score</th>
    </tr>
    <tr>
      <td>Baseline (Dense)</td>
      <td>단일 Dense 레이어</td>
      <td>2.341</td>
      <td>0.427</td>
      <td>0.682</td>
    </tr>
    <tr>
      <td>LSTM (Basic)</td>
      <td>단일 LSTM 레이어 + Dense</td>
      <td>2.298</td>
      <td>0.412</td>
      <td>0.701</td>
    </tr>
    <tr>
      <td>LSTM (Advanced)</td>
      <td>다중 LSTM + Dropout + Dense</td>
      <td>2.125</td>
      <td>0.384</td>
      <td>0.762</td>
    </tr>
    <tr>
      <td>CNN 1D</td>
      <td>Conv1D + Flatten + Dense</td>
      <td>2.268</td>
      <td>0.401</td>
      <td>0.712</td>
    </tr>
  </table>
</div>

## 📈 재고 최적화 결과

### 최적 안전재고량 결정

<div align="center">
  <h4>최종 재고 평가 결과</h4>
  <table>
    <tr>
      <th>상품</th>
      <th>최적 안전재고량</th>
      <th>일평균 재고량</th>
      <th>일평균 재고금액($)</th>
      <th>일평균 재고회전율</th>
      <th>기회손실 수량</th>
    </tr>
    <tr>
      <td>Product 3 (Beverage)</td>
      <td>15</td>
      <td>2606.167</td>
      <td>20849.336</td>
      <td>7.450</td>
      <td>136093.0</td>
    </tr>
    <tr>
      <td>Product 12 (Milk)</td>
      <td>12</td>
      <td>2006.087</td>
      <td>12036.522</td>
      <td>12.216</td>
      <td>160945.0</td>
    </tr>
    <tr>
      <td>Product 42 (Agricultural products)</td>
      <td>5</td>
      <td>1316.906</td>
      <td>6584.530</td>
      <td>0.301</td>
      <td>0.0</td>
    </tr>
  </table>
</div>

## 📝 비즈니스 인사이트 및 결론

### 💡 상품별 특성 및 재고 전략

#### 1. Beverage (Product 3)
- **판매 패턴**: 주말에 판매량 급증, 요일별 변동성 큼
- **재고 전략**: 주말 판매를 위한 목요일/금요일 재고 보충 필요
- **주요 도전**: 안전재고가 증가해도 기회손실 감소가 미미함
- **권장 사항**: 수요 예측 정확도 향상에 주력, 요일별 차별화된 재고 전략 필요

#### 2. Milk (Product 12)
- **판매 패턴**: 주말 판매 증가 및 12월 판매 피크
- **재고 전략**: 높은 재고회전율을 고려한 신선도 관리 필요
- **주요 도전**: 높은 기회손실 문제 해결 필요
- **권장 사항**: 수요 예측과 안전재고 최적화 병행, 방문객수와 연계한 발주량 조절

#### 3. Agricultural Products (Product 42)
- **판매 패턴**: 명확한 계절성, 7월 피크 및 1월 저점
- **재고 전략**: 낮은 안전재고량으로도 효과적 관리 가능
- **주요 강점**: 기회손실 없이 관리 가능한 유일한 상품
- **권장 사항**: 계절적 추세를 활용한 장기 재고 계획 수립

### 📋 향후 개선 방향

1. **예측 모델 개선**
   - 테스트 데이터에서의 성능 하락 원인 분석 및 해결
   - 외부 변수(프로모션, 계절 요인 등) 추가 반영

2. **안전재고 산출 방식 개선**
   - 상품별 특성을 고려한 동적 안전재고 모델 개발
   - 재고비용과 기회손실을 동시에 최적화하는 알고리즘 개발

3. **실시간 예측 시스템 구축**
   - 데이터 자동 수집 및 예측 시스템 구현
   - 일간 데이터 업데이트에 따른 예측 자동화

4. **상품 간 상관관계 분석**
   - 상품 간 판매 패턴 관계를 모델에 반영
   - 카테고리 전체를 고려한 통합 재고 전략 수립
