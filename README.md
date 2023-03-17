<h2>신체검사 데이터용 클래스 배열에서 평균키과 시력의 분포 구하기</h2>

클래스 배열을 통해서 평균 키와 시력의 분포를 구하는 알고리즘입니다

```java
class PhysicalExamination {
    static final int VMAX = 21;
    static class PhyscData{
        String name;
        int height;
        double vision;

        PhyscData(String name, int height, double vision){
            this.name = name;
            this.height = height;
            this.vision = vision;
        }
    }
```
* VMAX 값이 변경기 되면 안되기 때문에 final 이라는 키워드를 붙여 주고 Static 변수는 클래스 변수입니다. 
객체를 생성하지 않고도 Static 자원에 접근이 가능합니다.
클래스형 변수를 사용할 떄는 먼저 클래스형 변수(실체를 참조하는 변수)를 만들고, 실체인 클래스 인스턴스를 
생성 해줍니다 . this키워드를 하여 위에 선언한 name을 매개변수에 있는 name과 같게 해줍니다.




```java
    static double avaHeight(PhyscData[]dat){
        double sum = 0;

        for(int i =0; i < dat.length; i++)
            sum += dat[i].height;
            return sum / dat.length;
    }
```

* 키 평균을 구하는 메소드 이다

```java
        static void distVision(PhyscData[] dat, int[] dist){
        int i = 0;
        dist[i] = 0;
        for (i=0; i< dat.length; i++)
            for (i=0; i< dat.length; i++)
                if (dat[i].vision >= 0.0 && dat[i].vision <= VMAX / 10.0)
                    dist[(int)(dat[i].vision * 10)]++;
    }
```

 * 시력 분포를 구하는 메소드 이다. 
 PhyscData형 배열과 정수형 배열을 인자로 받는다 
    for문에서 dat 길이 만큼 반복을 하고 if문을 통해서 dat[i].vision 의 값이 0.0 ~ VMAX / 10.0 사이에 있는지 확인한 뒤     
    dist[(int)(dat[i].vision * 10)]++; 를 통해 배열의 인덱스를 구한다.
 
 
 
  ```java
     public static void main(String[] args) {

         PhyscData[] x = {
                 new PhyscData("강민하", 162, 0.3),
                 new PhyscData("김찬우", 173, 0.7),
                 new PhyscData("박준서", 175, 2.0),
                 new PhyscData("유서범", 171, 1.5),
                 new PhyscData("이수연", 168, 0.4),
                 new PhyscData("장경오", 174, 1.2),
                 new PhyscData("황지안", 169, 0.0)
         };
         int[] vdist = new int [VMAX];

         System.out.println("신체검사 리스트");
         System.out.println("이름 키 시력");
         System.out.println("===============");

         for (int i = 0; i < x.length; i++)
             System.out.printf("%-6s%3d%5.1f\n",x[i].name,x[i].height,x[i].vision);
         System.out.printf("\n평균 키 : %5.1fcm\n", avaHeight(x));

         distVision(x, vdist);
         System.out.println("\n시력 분포");
         for (int i = 0; i<VMAX; i++)
             System.out.printf("%3.1f~ : %2d명\n", i / 10.0, vdist[i]);
     }
}
```
* 인스턴스 선언과 name,height,vision 값을 넣어줍니다 그 아래코드는 출력이 되는 값을 불러옵니다 
 젤 위의 코드의 int[] vdist = new int [VMAX]는 21개의 배열을 모두 불러오는 변수입니다. 
 그 아래 코드는 신체검사 이름 키 시력 을 출력을 해준다 for 문으로 배열을 와줌으로서 위에 있는 인스턴스의 이름 키 시력을
 불러온다 따라서 평균키 시력 분포를 결과값에 출력합니다


