
```
package aleikum;
import robocode.*;
import java.awt.Color;

// API help : https://robocode.sourceforge.io/docs/robocode/robocode/Robot.html

/**
 * Salam - a robot by (your name here)
 */
public class Salam extends Robot
{
	/**
	 * run: Salam's default behavior
	 */
 public void run() {
        // Initialization of the robot should be put here
        // After trying out your robot, try uncommenting the import at the top,
        // and the next line:
        // setColors(Color.blue,Color.blue,Color.grey,Color.red,Color.green); // body,gun,radar
        // Robot main loop
		
		setBodyColor(new Color(255, 255, 255));
        setGunColor(new Color(120, 25, 41));
        setRadarColor(new Color(44, 199, 36));
        setScanColor(new Color(214, 0, 247));
        setBulletColor(new Color(0, 243, 247));
		

        while(true) { //next 4 lines with any behavior you would like
            double distance = Math.random()*300;
            double angle = Math.random()*45;
            turnRight(angle);
            ahead(distance);
            ahead(100);
            turnGunRight(45);
            back(100);
            turnGunRight(45);
        }
    }

    /**
     * onScannedRobot: What to do when you see another robot
     */
    public void onScannedRobot(ScannedRobotEvent e) {
        // Replace the next line with any behavior you would like
        double distance = e.getDistance();

       if(distance > 800) //this conditions adjust the fire force according the distance of the scanned robot.
		fire(5);
    else if(distance > 600 && distance <= 800)
        fire(4);
    else if(distance > 400 && distance <= 600)
        fire(3);
    else if(distance > 200 && distance <= 400)
        fire(2);
    else if(distance < 200)
        fire(1);
    }

    /**
     * onHitByBullet: What to do when you're hit by a bullet
     */
    public void onHitByBullet(HitByBulletEvent e) {
        // Replace the next line with any behavior you would like
        back(10);
    }

    /**
     * onHitWall: What to do when you hit a wall
     */
   public void onHitWall(HitWallEvent e){
    double bearing = e.getBearing(); //get the bearing of the wall
    turnRight(-bearing); //This isn't accurate but release your robot.
    ahead(100); //The robot goes away from the wall.
}
}
```
