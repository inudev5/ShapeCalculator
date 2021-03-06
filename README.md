# W2 OOP

## 팩토리 메서드 패턴

팩토리 메서드는 객체의 생성코드를 별도의 클래스/메서드에서 관리하는 것이다. 어느 한 타입이 존재할 때, 그 객체를 생성하는 책임이 본인이나 상속으로 연관된 클래스에게 있다면, 관계가 꼬리를 무는 꼴이 되기 때문에 관계를 파악하기 어려워질 뿐더라 객체간의 결합이 강결합으로 묶여 유지보수가 힘들어진다. 따라서 생성하는 책임, 혹은 타입을 판단하는 책임을 외부에 위임하여 객체를 대신 생성하게 한다면, 이러한 강결합의 문제를 피할 수가 있게 된다. 이러한 역할을 하는 별도의 클래스/ 메서드를 팩토리 클래스/메서드라고 부르며, 아래 코드에서는 별도의 클래스에 객체 생성없이 사용할 수 있도록 `static`키워드로 메서드를 가지게 되었다. 타입 생성하는 부분은 SOLID의 OCP 원칙에 따라 수정에는 닫혀있고, 케이스의 확장에는 열려있어야 하는 것이 원칙이다. 따라서, 현재의 if문이나 else문/ switch문 보다 라우팅 테이블/ 라우터를 만들어 구현하는 것이 바람직하다.
```javascript
class ShapeFactory{
    static createShape(points:Point[]):Line|Tri|Rectangle|Polygon{
        let shape;
        if(points.length===2){shape = new Line(points)}
        if(points.length===3){shape = new Tri(points)}
        if(points.length===4){shape = new Rectangle(points)}
        if(points.length>=5){shape = new Polygon(points)}
        if (shape===undefined){throw 'not defined'}
        return shape;
    }
}

```
## 추상 클래스 상속

Shape 클래스는 모든 도형 클래스들의 부모가 되는 클래스로 abstract 클래스이다. 구현해야할 추상 메서드로는 area메서드가 있으며 직선 클래스는 이 부분을 구현할 수 없으므로 throw하였다. 자바스크립트는 런타임언어로 가장 빨리 에러를 내는 방법은 throw 뿐이다. 해당 에러는 콘솔에서 catch되어 다시 반복되므로 내결합성을 가진다. 


print() 메서드는 모든 클래스가 공통적으로 가지고 있으므로 부모 클래스에서 한번만 구현하였다. printCalc 클래스는 거리혹은 넓이를 출력하는 메서드로 Line 클래스에서만 오버라이딩 되도록 하였다.(길이와 넓이의 출력만 다르게 처리)






