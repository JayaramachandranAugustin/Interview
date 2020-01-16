# Flood fill algorithm

Author - [Jayaramachandran Augustin](https://www.linkedin.com/in/jayaramachandran-augustin-bbb754109/).

In this lesson, we will see about flood fill algorithm. Flood fill algorithm helps in visiting each and every point in a given area. It determines the area connected to a given cell in a multi-dimensional array.

Check whether the selected position is colored with the old color or not, if not, we will skip the flood fill. Otherwise, we will fill that pixel with new color and recursively perform for all its four neighbors.

The flood fill can be done 4 directions or 8 directions.

Application of flood fill algorithms

1. Bucket Fill in Paint:
2. Solving a Maze:
3. Minesweeper:


```Java
import java.util.LinkedList;
import java.util.Queue;

public class FloodFill {
	public void floodFill(int[][] square,int r,int c,int newValue,int oldValue) {
		if(r<0||c<0||r>=square.length||c>=square[0].length) return;
		if(square[r][c]!=oldValue)return;
		square[r][c]=newValue;

		floodFill(square,r+1,c,newValue,oldValue);
		floodFill(square,r-1,c,newValue,oldValue);
		floodFill(square,r,c+1,newValue,oldValue);
		floodFill(square,r,c-1,newValue,oldValue);
	}

	public void floodFillQueue(int[][] square,int r,int c,int newValue,int oldValue) {
		if(checkBoundaryandValue(r, c, square,oldValue)) return;
		Queue<Point> queue=new LinkedList<>();
		square[r][c]=newValue;
		int[][] boundaries= {{1,0},{-1,0},{0,1},{0,-1}};
		queue.add(new Point(r,c));
		while(!queue.isEmpty()) {
			Point p=queue.poll();
			for(int[] boundary:boundaries) {
				if(!checkBoundaryandValue(p.r+boundary[0], p.c+boundary[1], square, oldValue)) {
					queue.add(new Point(p.r+boundary[0], p.c+boundary[1]));
					square[p.r+boundary[0]][p.c+boundary[1]]=newValue;
				}
			}

		}

	}

	public boolean checkBoundaryandValue(int r,int c,int[][] square,int oldValue) {
		if(r<0 || c<0 || r>=square.length||c>=square[0].length ||square[r][c]!=oldValue) return true;
		return false;
	}

	public static void main(String[] args) {
		int[][] square= {{0,0,0,1,1,1,1,1,0,0,0,0},
				{0,0,1,1,1,1,1,1,1,1,1,0},
				{0,0,2,2,2,4,4,5,4,0,0,0},
				{0,2,4,2,4,4,4,5,4,4,4,0},
				{0,2,4,2,2,4,4,4,2,4,4,4},
				{0,2,2,4,4,4,4,2,2,2,2,0},
				{0,0,0,4,4,4,4,4,4,4,0,0},
				{0,0,1,1,6,1,1,1,0,0,0,0},
				{0,1,1,1,6,1,1,6,1,1,1,0},
				{1,1,1,1,6,6,6,6,1,1,1,1},
				{4,4,1,6,3,6,6,3,6,1,4,4},
				{4,4,4,6,6,6,6,6,6,4,4,4},
				{4,4,6,6,6,6,6,6,6,6,4,4},
				{0,0,6,6,6,0,0,6,6,6,0,0},
				{0,2,2,2,0,0,0,0,2,2,2,0},
				{2,2,2,2,0,0,0,0,2,2,2,2}};


		int r=11,c=6,newValue=7;
		int oldValue=square[r][c];
		FloodFill floodFill=new FloodFill();
		floodFill.floodFillQueue(square,r,c,newValue,oldValue);
		floodFill.printSquare(square);

	}

	public void printSquare(int[][] square) {
		for(int i=0;i<square.length;i++) {
			for(int j=0;j<square[0].length;j++) {
				System.out.print(square[i][j]+" ");
			}
			System.out.println();
		}
		System.out.println();
	}
}
class Point{
	int r;
	int c;
	Point(int r,int c){
		this.r=r;
		this.c=c;
	}
}
```
