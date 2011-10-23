package chapter15_recursion;
// Fig. 15.22: FractalJPanel.java
// FractalJPanel demonstrates recursive drawing of a fractal.
import java.awt.Color;
import java.awt.Dimension;
import java.awt.Graphics;
import java.lang.Math;
import java.math.BigDecimal;
import java.util.Random;

import javax.swing.JPanel;

public class FractalJPanel extends JPanel {
	/**
	 * version:1.0
	 */
	private static final long serialVersionUID = 1L;
	private Color color; // stores color used to draw fractal
	private int level; // stores current level of fractal
	private final int WIDTH = 900; // defines width of JPanel
	private final int HEIGHT = 800; // defines height of JPanel

// set the initial fractal level to the value specified
// and set up JPanel specifications
public FractalJPanel( int currentLevel ) {
	color = Color.GREEN; // initialize drawing color to blue
	level = currentLevel; // set initial fractal level
	setBackground( Color.BLACK );
	setPreferredSize( new Dimension( WIDTH, HEIGHT ) );
} // end FractalJPanel constructor

// draw fractal recursively
public void drawFractal( int level, int xA, int yA, int xB,
							int yB, Graphics g ) {
	// base case: draw a line connecting two given points
	if ( level == 0 )
		g.drawLine( xA, yA, xB, yB );
	else { // recursion step: determine new points, draw next level
	 // calculate midpoint between (xA, yA) and (xB, yB)
	 int xC = ( xA + xB ) / 2;
	 int yC = ( yA + yB ) / 2;
	 // calculate the fourth point (xD, yD) which forms an
	 // isosceles right triangle between (xA, yA) and (xC, yC)
	 // where the right angle is at (xD, yD)
	 int xD = xA + ( xC - xA ) / 2 - ( yC - yA ) / 2;
	 int yD = yA + ( yC - yA ) / 2 + ( xC - xA ) / 2;
	 // recursively draw the Fractal
	 drawFractal( level - 1, xD, yD, xA, yA, g );
	 drawFractal( level - 1, xD, yD, xC, yC, g );
	 drawFractal( level - 1, xD, yD, xB, yB, g );
	} // end else
} // end method drawFractal

public void drawFractal_alpha( int level, int xA, int yA, int xB,
		int yB, Graphics g ) {
// base case: draw a line connecting two given points
if ( level == 0 )
g.drawLine( xA, yA, xB, yB );
else { // recursion step: determine new points, draw next level
// calculate midpoint between (xA, yA) and (xB, yB)
int xC = ( xA + xB ) / 2;
int yC = ( yA + yB ) / 2;
// calculate the fourth point (xD, yD) which forms an
// isosceles right triangle between (xA, yA) and (xC, yC)
// where the right angle is at (xD, yD)
int xD = xA + ( xC - xA ) / 4 - ( yC - yA ) / 4;
int yD = yA + ( yC - yA ) / 4 + ( xC - xA ) / 4;
// recursively draw the Fractal
drawFractal_alpha( level - 1, xD, yD, xA, yA, g );
drawFractal_alpha( level - 1, xD, yD, xC, yC, g );
drawFractal_alpha( level - 1, xD, yD, xB, yB, g );
} // end else
} // end method drawFractal

public void drawFractal_beta(int level, int x, int y, 
		int width, int height, Graphics g) {
//base case 
	if ( level == 0 )
		g.drawOval(x, y, width, height);
	// calculate new origin
	else {
		int newX = x + width/2;
		width = width/2;
		int newY = y + height/2;
		height = height/2;
		drawFractal_beta(level-1, x, y, width, height, g);
		drawFractal_beta(level-1, newX, y, width, height, g);
//		drawFractal_beta(level-1, x, y, width, height, g);
		drawFractal_beta(level-1, x, newY, width, height, g);
//		drawFractal_beta(level-1, x, y, width, height, g);
		drawFractal_beta(level-1, newX, newY, width, height, g);
		drawFractal_beta(level-1, x, y, width, height, g);
	}
}

public void drawFractal_gamma(int level, int  x,  int y, int width, double n, Graphics g){
	//base case 
	if (level == 0){
	//	g.drawOval(x, y, (int) (width * Math.PI), width);
	//	g.drawOval(x, y, width, (int) (width * Math.PI));
		g.drawOval(x, y, width, width);
	}
	else {
		int radius = width/8;

		int newX = (int) (x + radius * Math.cos(n));
		int newY = (int) (y + radius * Math.sin(n));
		System.out.println(newX + "," + newY);
		drawFractal_gamma(level -1, x, y, width, n, g);
		drawFractal_gamma(level -1, newX, newY, width -radius, n / 2 * Math.PI * radius, g);
	}

}

public void drawFractal_zeta(int level, int  x,  int y, int width, double n, Graphics g){
	//base case 
	if (level == 0){
		g.drawOval(x, y, width, width);
	}
	else {
		drawFractal_zeta(level -1, x, y, width, n ,g);
		int radius = width/10;
		//set phase
		if (n > 2* Math.PI)
			n = 0;
		else
			n += 1/Math.PI;
		int ax = (int) (x + radius * Math.cos(n));
		int ay = (int) (y + radius * Math.sin(n));
		System.out.println(ax + "," + ay + "," + n);
		drawFractal_zeta(level -1, ax, ay, width, n, g);
	}

}

public void drawFractal_theta(int level, int  x,  int y, int width, double n, Graphics g){
/*	int ax, ay;
	Random rand = new Random(System.currentTimeMillis()+Thread.currentThread().getId());
	for (n = 0; n < 2 * Math.PI; n += rand.nextDouble()){
		ax= 400 + (int)(50 * Math.sin(n) * (Math.pow(Math.E, Math.cos(n)) - 2 * Math.cos(4*n) 
				- Math.pow(Math.sin(n/12), 5)));
		ay = 400 + (int) (50 * Math.cos(n) * (Math.pow(Math.E, Math.cos(n)) - 2 * Math.cos(4*n) 
				- Math.pow(Math.sin(n/12), 5)));
		g.fillOval(ax, ay, width, width);
		System.out.println(ax + "," + ay + "," + n);
		level --;
	}	
	
*/	
//base case 
	if (level == 0){
		g.fillOval(x, y, width, width);
	}
	else {
		drawFractal_theta(level -1, x, y, width, n ,g);
	///	int radius = width * 100;
		//set phase
		Random rand = new Random(System.currentTimeMillis()+Thread.currentThread().getId());
		if (n > 2 * Math.PI)
			n = 0;
		else 
			n += rand.nextDouble();
//		a simple helix?
		int ax = 400 + (int) (50* width * Math.cos(n));
		int ay = 400 + (int)  (50* width * Math.sin(n)); 
		System.out.println(ax + "," + ay + "," + n);
		drawFractal_theta(level -1, ax, ay, width, n, g);
//		butterfly curve
		 ax = 400 + (int)(50 * Math.sin(n) * (Math.pow(Math.E, Math.cos(n)) - 2 * Math.cos(4*n) 
				- Math.pow(Math.sin(n/12), 5)));
		 ay = 400 + (int) (50 * Math.cos(n) * (Math.pow(Math.E, Math.cos(n)) - 2 * Math.cos(4*n) 
				- Math.pow(Math.sin(n/12), 5)));
		System.out.println(ax + "," + ay + "," + n);
		drawFractal_theta(level -1, ax, ay, width, n, g);
	}

}

public void paintComponent( Graphics g ){
	super.paintComponent( g );
	// draw fractal pattern
	g.setColor( color );
//	drawFractal_alpha( level, 100, 190, 590, 600, g );
//	drawFractal_beta(level, 10, 10, 800, 800, g);
//	drawFractal_gamma(level, 10, 120, 700, 1, g);
//	drawFractal_zeta(level, 380, 150, 250, 0, g);
	drawFractal_theta(level, 380, 400, 3, 0, g);
}// end method paintComponent

// set the drawing color to c
public void setColor( Color c ){
	color = c;
} // end method setColor

// set the new level of recursion
public void setLevel( int currentLevel )
{
level = currentLevel;
} // end method setLevel

// returns level of recursion
public int getLevel()
{
return level;
} // end method getLevel

}
	
