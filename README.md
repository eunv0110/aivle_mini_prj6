# 유통 판매량 예측 및 재고 최적화

## 📋 프로젝트 개요

<div align="center">
  <h3><i>"시계열 데이터 기반 판매량 예측 및 재고 최적화"</i></h3>
</div>

본 프로젝트는 유통 매장의 상품별 판매량을 예측하고 이를 기반으로 재고를 최적화하는 모델을 개발하는 것을 목표로 합니다. 효율적인 재고 관리는 과재고로 인한 자금 묶임과 재고 부족으로 인한 기회 손실을 방지하여 매장 운영의 효율성을 높이는 데 핵심적입니다.

## 🎯 문제 정의

```
❓ 유통 매장에서 핵심 상품에 대한 수요량을 예측하고 재고를 최적화할 수 있는가?
```

### 재고 최적화가 중요한 이유:
- 🔹 과재고 시 자금이 묶여 유동성 문제 발생
- 🔹 재고 부족 시 판매 기회 손실
- 🔹 리드타임을 고려한 정확한 발주 계획 필요
- 🔹 상품별 특성에 맞는 맞춤형 재고 관리 필요

## 📊 데이터 소개

<table>
  <tr>
    <th align="center" width="20%">분석 대상</th>
    <td>유통 매장 핵심 상품 판매 데이터</td>
  </tr>
  <tr>
    <th align="center">데이터 구성</th>
    <td>
      <ul>
        <li>sales_train.csv, sales_test.csv: 판매 정보</li>
        <li>orders_train.csv, orders_test.csv: 일별 매장별 고객 방문 수</li>
        <li>oil_price_train.csv, oil_price_test.csv: 일별 유가</li>
        <li>products.csv: 상품 기본 정보</li>
        <li>stores.csv: 매장 기본 정보</li>
      </ul>
    </td>
  </tr>
  <tr>
    <th align="center">대상 상품</th>
    <td>
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
    </td>
  </tr>
</table>

## 🛠️ 프로젝트 수행 단계

<div>
  <div>
    <h3>1️⃣ 데이터 탐색 및 가설 도출</h3>
    <ul>
      <li>시계열 패턴 확인</li>
      <li>요일별 판매 패턴 분석</li>
      <li>휘발유 가격과 판매량 관계 분석</li>
      <li>방문 고객수와 판매량 관계 분석</li>
      <li>시계열 데이터 분해 및 특성 파악</li>
    </ul>
  </div>
  <div>
    <h3>2️⃣ 데이터 전처리 및 기초 모델링</h3>
    <ul>
      <li>상품별 데이터 파이프라인 구축</li>
      <li>시계열 특성 생성 및 변환</li>
      <li>기초 모델 구축 및 평가
        <ul>
          <li>기본 Dense 모델 구현</li>
          <li>LSTM 모델 구현</li>
          <li>CNN 모델 구현</li>
        </ul>
      </li>
      <li>모델별 성능 비교 및 평가</li>
    </ul>
  </div>
  <div>
    <h3>3️⃣ 모델링 및 비즈니스 평가</h3>
    <ul>
      <li>최적 모델 선정 및 성능 개선</li>
      <li>파이프라인 함수 구현</li>
      <li>테스트 데이터 예측 및 성능 평가</li>
      <li>재고 시뮬레이션 구현</li>
      <li>안전재고량 최적화</li>
      <li>비즈니스 평가 지표 분석</li>
    </ul>
  </div>
</div>

## 📈 데이터 탐색 결과

### 📊 주요 패턴 분석

#### Product 3 - Beverage

- **요일별 판매 패턴**: 주말(토요일, 일요일)에 판매량이 증가하며, 평일 중에서는 월요일, 수요일, 금요일에 비교적 높은 판매량을 보임
- **휘발유 가격 관계**: 휘발유 가격 변동과 판매량 사이에 특별한 상관관계가 관찰되지 않음
- **연말 판매 증가**: 연말에는 고객 방문 수가 증가하며, 이에 따라 판매량도 평균적으로 증가하는 패턴을 보임
- **장기적 판매 추세**: 전체 기간에서 평균 판매량이 점진적으로 증가하는 추세를 보임

#### Product 12 - Milk

- **월별 판매 패턴**: 12월에 전체적인 판매량이 높으며, 특히 중순에 가장 높은 판매량이 관찰됨
- **방문자 수와 판매량 관계**: 방문자 수가 많아질수록 판매량도 증가하는 경향을 보임
- **주말 판매 증가**: 주말에는 평일보다 판매량이 높은 경향이 관찰됨
- **카테고리 내 비교**: 동일 카테고리 내에서 가장 높은 판매량을 기록

#### Product 42 - Agricultural products

- **계절적 패턴**: 7월(여름)에 판매량이 피크를 찍고, 1월(겨울)에 최저점을 기록하는 뚜렷한 계절적 패턴을 보임
- **시계열 분해**: 뚜렷한 계절성과 추세 요소가 관찰됨
- **공휴일 영향**: 공휴일과 주말에 판매량 증가 패턴이 관찰됨

## 📈 모델링 결과

### 📊 모델 성능 비교

#### Product 3 - Beverage
<div>
  <h4>상품 3 (Beverage) 모델 성능 비교</h4>
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
  <p><strong>최종 선택 모델: LSTM (Advanced)</strong></p>
  <ul>
    <li>다중 LSTM 계층 (32 -> 16 -> 8)</li>
    <li>Dropout 적용 (0.2)</li>
    <li>Early Stopping 및 Adam 옵티마이저 사용</li>
  </ul>
</div>

#### Product 12 - Milk
<div>
  <h4>상품 12 (Milk) 모델 성능 비교</h4>
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
      <td>1.872</td>
      <td>0.301</td>
      <td>0.725</td>
    </tr>
    <tr>
      <td>LSTM (Basic)</td>
      <td>단일 LSTM 레이어 + Dense</td>
      <td>1.583</td>
      <td>0.258</td>
      <td>0.792</td>
    </tr>
    <tr>
      <td>LSTM (Advanced)</td>
      <td>다중 LSTM + Dropout + Dense</td>
      <td>1.375</td>
      <td>0.221</td>
      <td>0.855</td>
    </tr>
    <tr>
      <td>CNN 1D</td>
      <td>Conv1D + Flatten + Dense</td>
      <td>1.621</td>
      <td>0.264</td>
      <td>0.781</td>
    </tr>
  </table>
  <p><strong>최종 선택 모델: LSTM (Advanced)</strong></p>
  <ul>
    <li>다중 LSTM 계층 (64 -> 32 -> 16)</li>
    <li>Dropout 적용 (0.2)</li>
    <li>Early Stopping 및 Adam 옵티마이저(learning_rate=0.005) 사용</li>
  </ul>
</div>

#### Product 42 - Agricultural products
<div>
  <h4>상품 42 (Agricultural Products) 모델 성능 비교</h4>
  <table>
    <tr>
      <th>모델</th>
      <th>설명</th>
      <th>MAE</th>
      <th>MAPE</th>
      <th>R² Score</th>
    </tr>
    <tr>
      <td>Baseline (Linear)</td>
      <td>선형 회귀</td>
      <td>1.258</td>
      <td>0.242</td>
      <td>0.721</td>
    </tr>
    <tr>
      <td>Random Forest</td>
      <td>랜덤 포레스트</td>
      <td>0.893</td>
      <td>0.172</td>
      <td>0.843</td>
    </tr>
    <tr>
      <td>LSTM (Basic)</td>
      <td>단일 LSTM 레이어 + Dense</td>
      <td>0.841</td>
      <td>0.163</td>
      <td>0.862</td>
    </tr>
    <tr>
      <td>LSTM (Advanced)</td>
      <td>128 units LSTM + Dense</td>
      <td>0.727</td>
      <td>0.139</td>
      <td>0.892</td>
    </tr>
  </table>
  <p><strong>최종 선택 모델: LSTM (Advanced)</strong></p>
  <ul>
    <li>단일 LSTM 레이어(128 units)</li>
    <li>Early Stopping 및 Model Checkpoint 적용</li>
    <li>Adam 옵티마이저(learning_rate=0.0005) 사용</li>
  </ul>
</div>

### 📊 테스트 데이터 성능 평가

<div>
  <h4>최종 모델의 테스트 데이터 성능</h4>
  <table>
    <tr>
      <th>상품</th>
      <th>MAE</th>
      <th>MAPE</th>
      <th>R² Score</th>
    </tr>
    <tr>
      <td>Product 3 (Beverage)</td>
      <td>6757.75</td>
      <td>0.540</td>
      <td>-2.600</td>
    </tr>
    <tr>
      <td>Product 12 (Milk)</td>
      <td>7919.61</td>
      <td>0.678</td>
      <td>-6.744</td>
    </tr>
    <tr>
      <td>Product 42 (Agricultural products)</td>
      <td>969.66</td>
      <td>8.812</td>
      <td>-4621.231</td>
    </tr>
  </table>
</div>

### 📊 재고 시뮬레이션 결과

#### Product 3 - Beverage
<div>
  <h4>안전재고량에 따른 재고 시뮬레이션 결과</h4>
  <table>
    <tr>
      <th>안전재고량</th>
      <th>일평균 재고량</th>
      <th>일평균 재고금액($)</th>
      <th>일평균 재고회전율</th>
      <th>기회손실 수량</th>
    </tr>
    <tr>
      <td>5</td>
      <td>2600.929</td>
      <td>20807.432</td>
      <td>7.468</td>
      <td>136273.0</td>
    </tr>
    <tr>
      <td>10</td>
      <td>2603.548</td>
      <td>20828.384</td>
      <td>7.459</td>
      <td>136183.0</td>
    </tr>
    <tr>
      <td>15</td>
      <td>2606.167</td>
      <td>20849.336</td>
      <td>7.450</td>
      <td>136093.0</td>
    </tr>
    <tr>
      <td>20</td>
      <td>2608.786</td>
      <td>20870.288</td>
      <td>7.441</td>
      <td>136003.0</td>
    </tr>
  </table>
</div>

#### Product 12 - Milk
<div>
  <h4>안전재고량에 따른 재고 시뮬레이션 결과</h4>
  <table>
    <tr>
      <th>안전재고량</th>
      <th>일평균 재고량</th>
      <th>일평균 재고금액($)</th>
      <th>일평균 재고회전율</th>
      <th>기회손실 수량</th>
    </tr>
    <tr>
      <td>5</td>
      <td>2002.435</td>
      <td>12014.610</td>
      <td>12.250</td>
      <td>161085.0</td>
    </tr>
    <tr>
      <td>10</td>
      <td>2005.043</td>
      <td>12030.258</td>
      <td>12.225</td>
      <td>160985.0</td>
    </tr>
    <tr>
      <td>15</td>
      <td>2007.652</td>
      <td>12045.912</td>
      <td>12.201</td>
      <td>160885.0</td>
    </tr>
    <tr>
      <td>20</td>
      <td>2010.261</td>
      <td>12061.566</td>
      <td>12.176</td>
      <td>160785.0</td>
    </tr>
  </table>
</div>

#### Product 42 - Agricultural products
<div>
  <h4>안전재고량에 따른 재고 시뮬레이션 결과</h4>
  <table>
    <tr>
      <th>안전재고량</th>
      <th>일평균 재고량</th>
      <th>일평균 재고금액($)</th>
      <th>일평균 재고회전율</th>
      <th>기회손실 수량</th>
    </tr>
    <tr>
      <td>5</td>
      <td>1316.906</td>
      <td>6584.530</td>
      <td>0.301</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>10</td>
      <td>1321.906</td>
      <td>6609.530</td>
      <td>0.285</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>15</td>
      <td>1326.906</td>
      <td>6634.530</td>
      <td>0.271</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>20</td>
      <td>1331.906</td>
      <td>6659.530</td>
      <td>0.258</td>
      <td>0.0</td>
    </tr>
  </table>
</div>

### 📈 최적 안전재고량 결정

<div>
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

## 📝 결론 및 시사점

### 💡 비즈니스 인사이트

1. **모델 성능과 실제 적용 간 격차**
   - 검증 데이터에서는 모든 모델이 좋은 성능을 보였으나, 테스트 데이터에서는 성능 하락 관찰
   - 실제 환경에서의 적용 시 추가적인 모델 튜닝과 외부 요인 반영 필요

2. **상품별 재고 전략 차별화**
   - Beverage(음료): 안전재고가 증가해도 기회손실 감소가 미미함, 수요 예측 정확도 향상이 우선 과제
   - Milk(우유): 높은 재고회전율을 보이나 기회손실이 큼, 수요 예측과 안전재고 최적화 모두 중요
   - Agricultural products(농산물): 유일하게 기회손실이 0인 제품으로, 현 모델로도 효과적 관리 가능

3. **재고 비용과 기회손실의 균형**
   - 단순히 안전재고량 증가만으로는 기회손실 해소에 한계가 있음
   - 예측 정확도 향상과 안전재고량 최적화를 병행해야 효과적인 재고 관리 가능

4. **농산물의 특이성**
   - 농산물(Product 42)의 경우, 계절적 패턴이 뚜렷하여 예측이 상대적으로 용이
   - 낮은 재고회전율에도 불구하고 기회손실 없이 관리 가능한 유일한 상품

## 🧠 프로젝트에서 배운 점

1. **시계열 데이터 분석**
   - 시계열 데이터의 분해와 패턴 인식 방법
   - 요일, 월별, 계절별 패턴의 중요성

2. **딥러닝 모델 최적화**
   - LSTM 모델의 효과적인 구조 설계
   - Dropout, Early Stopping 등 과적합 방지 기법 적용

3. **재고 최적화 접근법**
   - 재고 수준과 기회손실 사이의 균형점 찾기
   - 상품별 특성에 맞는 안전재고 설정의 중요성

4. **데이터 파이프라인 구축**
   - 원시 데이터에서 모델 입력까지의 일관된 처리 과정 구축
   - 상품별 특성에 맞는 전처리 방법 적용

## 🛠️ 기술 스택

- **언어**: Python
- **데이터 처리**: Pandas, NumPy
- **시각화**: Matplotlib, Seaborn
- **머신러닝**: Scikit-learn, TensorFlow, Keras
- **시계열 분석**: Statsmodels

## 📋 향후 개선 방향

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
