import random, os, sys

'''
任务描述：
1.定义一个单张扑克类（考虑需要哪些属性），定义一个一副扑克牌类，该类包含一个单张扑克对象的数组（不考虑大小王）。实现一个模拟扑克发牌洗牌的算法；
2.电脑随机发出5张牌，判断是以下哪种牌型？（提示，利用Map，List，Set等各种集合的特性可以简化判断）
'''

class Card():
    # 单张扑克类(Card)，属性有：花色(color)和值(valuue)
    def __init__(self, color='red', value='1'):
        self.color = color
        self.value = value

    def getColor(self):
        return self.color

    def setColor(self, color):
        self.color = color

    def getValue(self):
        return self.value

    def setValue(self, value):
        self.value = value

    # 扑克牌转化，针对于特殊牌(字母牌AJQK)
    def toString(self):
        strValue = ""
        strTrans = {1: 'A', 11: 'J', 12: 'Q', 13: 'K'}
        if self.value in strTrans:
            strValue = strTrans[self.value]
        else:
            strValue = str(self.value)

        return self.color + strValue

# 一副扑克牌类，不包含大小王
class Poke():
    def __init__(self):
        colors = ('红桃', '黑桃', '方片', '梅花')
        values = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13)
        self.cards = []
        index = 0
        for i in range(4):
            for j in range(13):
                self.cards.append(Card())
                self.cards[index].setValue(values[j])
                self.cards[index].setColor(colors[i])
                index += 1

    #输出整副扑克牌
    def printCards(self):
        index2 = 0;
        for i in self.cards:
            if (index2 % 13 == 0):
                print('\n');
            print(i.toString() + " ", end='');
            index2 += 1

    '''
    shuffle()是不能直接访问的，需要导入 random 模块，然后通过 random 静态对象调用该方法。
    不会生成新的列表，只是将原列表的次序打乱
    '''

    #洗牌
    def shuffle(self):
        random.shuffle(self.cards)

    # 抽出前五张扑克牌
    def getFiveCard(self):
        cardHands = []
        for i in range(5):
            cardHands.append(self.cards[i])
        return cardHands

    # 判断5张扑克牌的类型
    def pokeType(self, hands):
        bIsSameColor = False
        bIsShunzi = False
        col = []
        val = []
        colset = []
        valset = []
        for i in hands:
            col.append(i.getColor())
            val.append(i.getValue())

        colset = set(col)
        valset = set(val)

        if len(colset) == 1:
            bIsSameColor = True  # 同色

        if (max(valset) - min(valset) == 4) and len(valset) == 5:
            bIsShunzi = True  # 顺子

        if (bIsSameColor and bIsShunzi):
            print('同花顺')

        elif bIsSameColor:
            print('同花')

        elif bIsShunzi:
            print('顺子')

        elif len(valset) == 5:
            print('无对')

        elif len(valset) == 4:
            print('一对')


        else:
            num = []  # 不同值的个数统计集合
            for i in valset:
                num.append(val.count(i))
            if max(num) == 4:
                print('四条')
            elif 1 not in num:
                print('满堂红')
            elif max(num) == 3:
                print('三条')
            else:
                print('两对')
        return

def main(args):
    poke = Poke()
    poke.printCards()
    poke.shuffle()
    print('\n\n洗牌之后的扑克分布：')
    poke.printCards()
    hands = poke.getFiveCard()
    print('\n\n抽取的扑克牌是:\n')

    for i in range(5):
        print(hands[i].toString() + "  ", end='')

    print('\n\n牌型是:\n')
    poke.pokeType(hands)

if __name__ == '__main__':
    main(sys.argv)
