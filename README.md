# ass1
package geometry;

public class Circle {
    private double x;
    private double y;
    private double radius;

    public Circle() {
        this(0, 0, 1);
    }

    public Circle(double x, double y, double radius) {
        this.x = x;
        this.y = y;
        this.radius = radius;
    }

    public double getX() { return x; }
    public double getY() { return y; }
    public double getRadius() { return radius; }

    public double getArea() {
        return Math.PI * radius * radius;
    }

    public double getPerimeter() {
        return 2 * Math.PI * radius;
    }

    public boolean contains(double x, double y) {
        double d = Math.sqrt(Math.pow(x - this.x, 2) + Math.pow(y - this.y, 2));
        return d <= radius;
    }

    public boolean contains(Circle circle) {
        double d = Math.sqrt(Math.pow(circle.x - this.x, 2) + Math.pow(circle.y - this.y, 2));
        return d + circle.radius <= this.radius;
    }

    public boolean overlaps(Circle circle) {
        double d = Math.sqrt(Math.pow(circle.x - this.x, 2) + Math.pow(circle.y - this.y, 2));
        return d < (this.radius + circle.radius) && !contains(circle) && !circle.contains(this);
    }
}