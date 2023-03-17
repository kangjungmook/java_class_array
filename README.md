<h2>신체검사 데이터용 클래스 배열에서 평균키과 시력의 분포 구하기</h2>


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
생성자를 호출할 때에는 원하는 생성자의 매개변수를 확인후 메소드를 호출하는 것처럼 this.매개변수 의 형태로 한다.
생성자를 이용해서 벤버변수에 넣어준다

```java
    static double avaHeight(PhyscData[]dat){
        double sum = 0;

        for(int i =0; i < dat.length; i++)
            sum += dat[i].height;
            return sum / dat.length;
    }
        static void distVision(PhyscData[] dat, int[] dist){
        int i = 0;
        dist[i] = 0;
        for (i=0; i< dat.length; i++)
            for (i=0; i< dat.length; i++)
                if (dat[i].vision >= 0.0 && dat[i].vision <= VMAX / 10.0)
                    dist[(int)(dat[i].vision * 10)]++;
    }
  ```
* 
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
