public class Mondriaan {
  public static void walkUp(int nrOfStepsUp) {
   while (nrOfStepsUp > 0 && !inFrontOfWall()){
       step();
       nrOfStepsUp --;
   }
  }
  public static void walkSide(int nrOfStepsSide) {
      turnRight();
      while (nrOfStepsSide > 0 && !inFrontOfWall()){
          step();
          nrOfStepsSide --;
      }
  }

    public static void walkBackDown(int nrOfStepsUp) {
        turnRight();
        turnRight();
        while (nrOfStepsUp > 0 && !inFrontOfWall()){
            step();
            nrOfStepsUp --;
        }
    }
    public static void walkBackSide(int nrOfStepsSide) {
        turnRight();
        while (nrOfStepsSide > 0 && !inFrontOfWall()){
            step();
            nrOfStepsSide --;
        }
        turnRight();
    }

  public static void putBallsVertical( int nrOfBallsVertical) {
      if (inFrontOfWall()) {
          nrOfBallsVertical=0;
      }
      if (onBall()) {
          step();
      }
      else {
          while (nrOfBallsVertical > 0 && !inFrontOfWall() && !onBall()) {
              putBall();
              step();
              nrOfBallsVertical--;
          }
      }

  }
  public static void putBallsHorizontal(int nrOfBallsHorizontal) {
      if (onBall()) {
          step();
      }
      if (inFrontOfWall()) {
          nrOfBallsHorizontal= 0;
      }
      while (nrOfBallsHorizontal > 0 && !inFrontOfWall() && !onBall()) {
          putBall();
          step();
          nrOfBallsHorizontal--;
      }
  }
  public static void makeShape(int nrOfShape, int nrOfBallsHorizontal, int nrOfBallsVertical) {
      while(nrOfShape>0) {
          putBallsHorizontal(nrOfBallsHorizontal);
          turnRight();
          putBallsVertical(nrOfBallsVertical);
          turnRight();
          putBallsHorizontal(nrOfBallsHorizontal);
          turnRight();
          putBallsVertical(nrOfBallsVertical);
          nrOfShape--;
      }


  }


  public static void main(String[] args) {
    map("mondriaan.map");
    speed(100);
    int nrOfStepsUp = random(1 , 15);
    int nrOfShape = random(2 , 4);
    int nrOfBallsVertical = random(1 , 15);
    int nrOfBallsHorizontal = random(1 , 15);
    int nrOfStepsSide= random(1,15);
    //if(inFrontOfWall()) {nrOfBallsHorizontal= 0;}
    //walkUp(nrOfStepsUp);
  //walkSide(nrOfStepsSide);
   /* putBallsHorizontal(nrOfBallsHorizontal);
    turnRight();
    putBallsVertical(nrOfBallsVertical);
    turnRight();
    putBallsHorizontal(nrOfBallsHorizontal);
    turnRight();
    putBallsVertical(nrOfBallsVertical);*/
walkUp(nrOfStepsUp);
walkSide(nrOfStepsSide);
    makeShape(nrOfShape, nrOfBallsHorizontal, nrOfBallsVertical);
    walkBackDown(nrOfStepsUp);
    walkBackSide(nrOfStepsSide);
  }

}
