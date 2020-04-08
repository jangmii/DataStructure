# 2020-1 자료구조 4주차과제 - Array ADT(python)
class Array:  # 파이썬에서는 클래스를 사용가능하므로 구조체 대신 클래스로 쓰고, 기능들은 내장함수로 넣었음
    def __init__(self):
        self.data = []  # 실제 배열 값
        self.pos = -1  # 현재 위치
        self.size = 0  # 배열 크기

    def isEmpty(self): #비었는지 확인
        return not(self.size)

    def insert(self, new_data): #값 삽입
        self.data.insert(self.pos+1, new_data)
        self.size += 1
        return self.pos+1

    def delete(self):
        if(self.isEmpty()):
            print("UnderFlow Error: No value to delete.")  # 언더플로우 에러 출력
            return -1
        self.data.pop(self.pos)
        self.size -= 1
        if(self.size == 0):
            return -1
        return self.pos % self.size

    def traverse_front(self):
        if(self.isEmpty()):
            return -1
        return 0

    def traverse_rear(self):
        return self.size-1

    def get_data(self):
        if(self.isEmpty()):
            print("Error: no data exsits ")
            return '?'
        return self.data[self.pos]

    def replace(self, new_data):
        if(self.isEmpty()):
            print("Error: no data exsits")
            return
        self.data[self.pos] = new_data

    def empty(self):
        self.data.clear()
        self.size = 0
        self.pos = -1

    def move(self, new_position):
        if (new_position < 0 or new_position >= self.size):  # 범위 내 위치가 아니면
            printf("Error : It cannot be moved.")  # 에러 출력
            return self.pos  # 기존 위치 반환
        temp = self.data[self.pos]
        self.data.pop(self.pos)
        self.data.insert(new_position, temp)
        return new_position

    def data_count(self):
        return self.size

    def print(self):
        if(self.isEmpty()):
            print("empty array")
            return
        for i, x in enumerate(self.data):
            if(self.pos == i):
                print("(%c)" % x, end="")
            else:
                print(" %c " % x, end="")
        print()

    def next(self):
        if (self.pos+1 == self.size):
            print("OverFlow Error: Move to where the value exists.")
            return self.pos
        return self.pos+1

    def prev(self):
        if(self.pos <= 0):
            print("UnderFlow Error: Move to where the value exists.")
            return self.pos
        return self.pos-1

    def find(self, target_data):
        if not(target_data in self.data):
            print("No Exsits")
            return self.pos
        return ((self.data*2).index(target_data, self.pos+1)) % self.size

    def count(self, target_data):
        return self.data.count(target_data)

    def sort(self):
        self.data.sort()


def help():  # 가능한 명령어들 메뉴 보여주기
    print("============= H E L P =============\n")
    print("INSERT			: +(data)")
    print("DELETE			: -")
    print("TRAVERSE_FRONT\t\t: <")
    print("TRAVERSE_REAR\t\t: >")
    print("GET_DATA		: @")
    print("REPLACE			: =(data)")
    print("EMPTY			: E")
    print("MOVE 			: M(position)")
    print("MOVE FRONT		: M")
    print("MOVE END		: Mn")
    print("MOVE PREV		: MP")
    print("MOVE NEXT		: MN")
    print("PRINT			: L")
    print("PREV			: P")
    print("NEXT			: N")
    print("FIND			: F(data)")
    print("COUNT			: C(data)")
    print("SORT			: S")
    print("HELP			: H\n")
    print("** Spacing between commands")
    # 한줄에 들어온 명령어들을 ' '단위로 쪼개서 처리하므로 띄어쓰기 없으면 무시함.
    print("** Only one character for one data")  # 한글자씩만 들어감
    print("===================================\n")
    return


# MAIN
my_arr = Array()
help()
while(True):
    my_str = input(">> ")
    for order in my_str.split():
        # 파이썬에서는 문자열 끝에 널값이 없어서 order[1]참조시 문제가 생길 수 있으므로 공백을 넣어준다
        order += ' '
        if order[0] == '+':
            my_arr.pos = my_arr.insert(order[1])
        elif order[0] == '-':
            my_arr.pos = my_arr.delete()
        elif order[0] == '<':
            my_arr.pos = my_arr.traverse_front()
        elif order[0] == '>':
            my_arr.pos = my_arr.traverse_rear()
        elif order[0] == '@':
            print("Return : %c" % my_arr.get_data())
        elif order[0] == '=':
            my_arr.replace(order[1])
        elif order[0] == 'E':
            my_arr.empty()
        elif order[0] == 'M':
            if(order[1] == ' '):
                npos = 0
            elif(order[1] == 'n'):
                npos = my_arr.data_count()-1
            elif(order[1] == 'N'):
                npos = my_arr.next()
            elif(order[1] == 'P'):
                npos = my_arr.prev()
            else:
                order = order[1:]
                try:
                    npos = int(order)
                except:
                    print("enter 'n'/'N'/'P' or only integers after 'M'")
                    npos = -1
            my_arr.pos = my_arr.move(npos)
        elif order[0] == 'L':
            pass
        elif order[0] == 'N':
            my_arr.pos = my_arr.next()
        elif order[0] == 'P':
            my_arr.pos = my_arr.prev()
        elif order[0] == 'F':
            my_arr.pos = my_arr.find(order[1])
        elif order[0] == 'C':
            cnt = my_arr.count(order[1])
            print("There is(are) %d '%c'(s)" % (cnt, order[1]))
        elif order[0] == 'S':
            my_arr.sort()
        elif order[0] == 'H':
            help()
        else:
            print("Please enter the correct command.")
    my_arr.print()
