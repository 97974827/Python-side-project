### Android 

##### Layout, Widget

- 레이아웃 설명 참고 : https://coding-restaurant.tistory.com/86

- TextView 에서 왼쪽에 이미지 추가 

  - ```xml
    android:drawableLeft="@drawable/ic_thumb_up"
    ```



- ### 균등 분포

  각 하위 요소가 화면에서 동일한 크기의 공간을 사용하는 선형 레이아웃을 생성하려면 각 뷰에 대한 [`android:layout_height`](https://developer.android.com/reference/android/view/ViewGroup.LayoutParams#attr_android:layout_height)를 `"0dp"`로 설정하거나(세로 레이아웃의 경우) 각 뷰에 대한 [`android:layout_width`](https://developer.android.com/reference/android/view/ViewGroup.LayoutParams#attr_android:layout_width)를 `"0dp"`로 설정합니다(가로 레이아웃의 경우). 그런 다음 각 뷰에 대한 [`android:layout_weight`](https://developer.android.com/reference/android/widget/LinearLayout.LayoutParams#attr_android:layout_weight)를 `"1"`로 설정합니다.



- 구분선 넣기

- ```xml
  ?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:orientation="vertical"
      tools:context="com.tistory.itpangpang.viewpagerex.MainActivity">
  
      <LinearLayout
          android:id="@+id/ll"
          android:layout_width="match_parent"
          android:layout_height="50dp"
          >
          <TextView
              android:layout_width="0dip"
              android:layout_height="match_parent"
              android:layout_weight="1"
              android:textSize="20dp"
              android:gravity="center"
              android:text="공지사항"/>
          <View
              android:layout_width="2dp"
              android:layout_height="match_parent"
              android:background="#BDBDBD"/>
          <TextView
              android:layout_width="0dip"
              android:layout_height="match_parent"
              android:layout_weight="1"
              android:textSize="20dp"
              android:gravity="center"
              android:text="게시판"/>
          <View
              android:layout_width="2dp"
              android:layout_height="match_parent"
              android:background="#BDBDBD"/>
          <TextView
              android:layout_width="0dip"
              android:layout_height="match_parent"
              android:layout_weight="1"
              android:textSize="20dp"
              android:gravity="center"
              android:text="오시는길"/>
      </LinearLayout>
  
      <View
          android:layout_below="@+id/ll"
          android:layout_width="match_parent"
          android:layout_height="2dp"
          android:layout_centerInParent="true"
          android:background="#BDBDBD"
          />
  </RelativeLayout>
  
  
  출처: https://itpangpang.xyz/298 [ITPangPang]
  ```



- 스크롤 추가 
  - 레이아웃 자체를 `<ScrollView>`로 감싸면 됨





#### 영화정보 디자인

```xml
<?xml version="1.0" encoding="utf-8"?>

<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">


        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:background="@drawable/background">

            <ImageView
                android:layout_width="150dp"
                android:layout_height="200dp"
                android:src="@drawable/image11"
                android:layout_marginTop="10dp"
                android:layout_marginBottom="20dp"/>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                android:layout_margin="30dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:orientation="horizontal">

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:text="군도"
                        android:textSize="24dp"
                        android:textStyle="bold"
                        android:textColor="#ffffff"/>

                    <ImageView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:src="@drawable/ic_15"
                        android:layout_marginLeft="10dp"/>

                </LinearLayout>

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:text="2014.07.23 개봉\n액션 / 137분"
                    android:textSize="18dp"
                    android:textColor="#ffffff"/>

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:orientation="horizontal">

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:drawableLeft="@drawable/ic_thumb_up"
                        android:layout_marginTop="20dp"
                        android:text=" 15     "
                        android:textStyle="bold"
                        android:textSize="24dp"
                        android:textColor="#ffffff"
                        />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:drawableLeft="@drawable/ic_thumb_down"
                        android:text=" 1"
                        android:layout_marginTop="20dp"
                        android:textStyle="bold"
                        android:textSize="24dp"
                        android:textColor="#ffffff"
                        />
                </LinearLayout>

            </LinearLayout>

        </LinearLayout>

        <!-- 칸 나누기   -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="100dp"
            >
            <TextView
                android:layout_width="0dip"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:textSize="20dp"
                android:gravity="center"
                android:text="예매율\n 5위 1.8%"/>
            <View
                android:layout_width="2dp"
                android:layout_height="match_parent"
                android:background="#BDBDBD"/>

            <LinearLayout
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:orientation="vertical">

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="match_parent"
                    android:layout_weight="1"
                    android:textSize="20dp"
                    android:gravity="center"
                    android:layout_marginTop="20dp"
                    android:paddingLeft="60dp"
                    android:text="평점\n"
                    />

                <RatingBar
                    style="@style/Widget.AppCompat.RatingBar.Small"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:numStars="5"
                    android:rating="4.5"
                    android:layout_marginLeft="15dp"
                    />

            </LinearLayout>

            <TextView
                android:layout_height="wrap_content"
                android:layout_width="wrap_content"
                android:text="8.2"
                android:textSize="20dp"
                android:gravity="center"
                android:layout_marginTop="42dp"
                android:layout_marginRight="10dp"
                android:paddingLeft="15dp"
                />

            <View
                android:layout_width="2dp"
                android:layout_height="match_parent"
                android:background="#BDBDBD"/>
            <TextView
                android:layout_width="0dip"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:textSize="20dp"
                android:gravity="center"
                android:text="누적관객수\n 839,399명"/>
        </LinearLayout>

        <View
            android:layout_width="match_parent"
            android:layout_height="2dp"
            android:layout_centerInParent="true"
            android:background="#BDBDBD"
            />
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="10dp"
            android:orientation="horizontal"
            android:background="#eeeeee">

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:layout_marginTop="10dp"
            android:layout_marginLeft="10dp">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="줄거리"
                android:textSize="20dp"
                android:textStyle="bold"
                android:layout_centerVertical="true"
                android:textColor="#2d2f31"
                />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="15dp"
                android:text="군도, 백성을 구하라!
                                \n양반과 탐관오리들의 착취가 극에 달했던 조선 철종 13년. \n힘 없는 백성의 편이 되어 세상을 바로잡고자 하는 의적떼인\n군도(群盜), 지리산 추설이 있었다.\n\n쌍칼 도치 vs 백성의 적 조윤\n잦은 자연재해, 기근과 관의 횡포까지 겹쳐 백성들의 삶이\n날로 피폐해져 가는 사이, 나주 대부호의 서자로 조선\n최고의 무관 출신인 조윤은 극악한 수법으로 양민들을 수탈,\n삼남지방 최고의 대부호로 성장한다. 한편 소, 돼지를 잡아\n근근이 살아가던 천한 백정 돌무치는 죽어도 잊지 못할\n끔찍한 일을 당한 뒤 군도에 합류. 지리산 추설의 신 거성(新\n巨星) 도치로 거듭난다.\n\n뭉치면 백성, 흩어지면 도적!\n망할 세상을 뒤집기 위해, 백성이 주인인 새 세상을 향해\n도치를 필두로 한 군도는 백성의 적, 조윤과 한 판 승부를\n시작하는데...\n"
                android:textSize="16dp"
                android:layout_centerVertical="true"
                />

            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:textSize="16dp"
                android:textStyle="bold"
                />

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="10dp"
            android:orientation="horizontal"
            android:background="#eeeeee">
        </LinearLayout>

        <!-- 출연진 정보  -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="10dp"
                android:layout_marginLeft="5dp"
                android:text="감독/출현"
                android:textColor="#2d2f31"
                android:textStyle="bold"
                android:textSize="15dp" />

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="40dp">
                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:layout_marginLeft="10dp"
                    android:text="감독 "
                    android:textColor="#2d2f31"
                    android:textStyle="bold"
                    android:textSize="15dp"/>

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:text=" 윤종빈"
                    android:textSize="15dp"/>
            </LinearLayout>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="40dp">

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_marginLeft="10dp"
                    android:text="출연 "
                    android:textColor="#2d2f31"
                    android:textSize="15dp"
                    android:textStyle="bold" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text=" 하정우(도치), 강동원(조윤)"
                    android:textSize="15dp" />
            </LinearLayout>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="10dp"
            android:orientation="horizontal"
            android:background="#eeeeee">
        </LinearLayout>

        <!--  한줄평    -->
        <RelativeLayout
            android:layout_width="wrap_content"
            android:layout_height="500dp">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="한줄평"
                android:layout_marginTop="10dp"
                android:layout_marginLeft="5dp"
                android:textColor="#2d2f31"
                android:textStyle="bold"
                android:textSize="25dp"/>

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_alignParentRight="true"
                android:layout_marginTop="10dp"
                android:layout_marginRight="10dp"
                android:drawableLeft="@drawable/ic_review_selected"
                android:gravity="right"
                android:text=" 작성하기"
                android:textColor="#ff5514"
                android:textSize="25dp"
                android:textStyle="bold" />

        </RelativeLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="70dp">

            <Button
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginLeft="10dp"
                android:layout_marginRight="10dp"
                android:text="모두보기"
                android:background="@drawable/linear_border_orange"
                />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <ImageView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:src="@drawable/ic_facebook"
                />

            <ImageView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginLeft="10dp"
                android:src="@drawable/ic_kakao"
                />

            <Button
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_marginLeft="10dp"
                android:layout_marginRight="10dp"
                android:text="예매하기"
                android:background="#e44414"
                android:textColor="#ffffff"
                />

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="10dp"
            android:orientation="horizontal"
            android:background="#eeeeee">
        </LinearLayout>

    </LinearLayout>
</ScrollView>
```







