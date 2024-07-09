# Mars-Rover-task
class Steam:
    def __init__(self,coordinate,Point):
        self.coordinate = coordinate
        self.coordinateX = 0
        self.coordinateY = 0
        self.Point = Point
        self.PointX = 0
        self.PointY = 0
        self.PointWay = 0
        self.WayList = "NESW"

    def Steamcoordinate(self):
        area = self.coordinate.split(" ")
        self.coordinateX = int(area[0])
        self.coordinateY = int(area[1])

    def SteamPoint(self):
        Find = False
        Point = self.Point.split(" ")
        self.PointX = int(Point[0])
        self.PointY = int(Point[1])
        while not Find:
            if self.WayList[self.PointWay] == Point[2]:
                Find = True
            else:
                self.PointWay += 1

class Movement(Steam):
    def __init__(self,coordinate,Point,Move):
        self.Move = Move
        super().__init__(coordinate,Point)

    def CalculatePoint(self):
        for indix in range(0,len(self.Move)):
            if self.Move[indix] == "R":
                self.PointWay += 1
            elif self.Move[indix] == "L":
                self.PointWay -= 1
            elif self.Move[indix] == "M":
                self.forword()
            else:
                pass
            self.ChangeWay()

    def ChangeWay(self):
        if self.PointWay > 3:
            self.PointWay = 0
        elif self.PointWay < 0:
            self.PointWay = 3


    def forword(self):
        if self.PointWay == 0:
            self.PointY += 1
        elif self.PointWay == 1:
            self.PointX += 1
        elif self.PointWay == 2:
            self.PointY -= 1
        else:
            self.PointX -= 1



    def Output(self):
        print(f"self.PointX,self.PointY,self.WayList[self.PointWay]")
        


done = ""
coordinate = str(input("Enter the coordinate"))
while done != "done":
    Point = str(input("Enter Start point"))
    Move = str(input("Enter Movement"))
    x = Movement(coordinate,Point,Move)
    x.SteamPoint()
    x.Steamcoordinate
    x.CalculatePoint()
    x.Output()
    done = input("If done Enter done")
