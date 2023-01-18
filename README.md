'''
# функция разбивает строки на отдельные символы в списке
def get_tpl(file_name, sep=','):
    with open(file_name) as f:
        lines = f.readlines()
    return [tuple(map(int, line.split(sep))) for line in lines]

# макс цена
def FindMaxWay(x, y, p, w): # p - цена ячейки, w - Путь 
  if x == rx-1 and y == ry-1:
      if p > price_lst[0]: # макс цена ячейки
       price_lst[0] = p
       price_lst[1] = w
  else:
      if x+1 < rx:          
        FindMaxWay(x+1, y, p+lab[y][x+1], w + 'x')
      if y+1 < ry:          
        FindMaxWay(x, y+1, p+lab[y+1][x], w + 'y')


def find_min_jumps(x, y, c, w):
    if x == dx-1 and y == dy-1:
        if c < resTwo[0]:
            resTwo[0] = c
            resTwo[1] = w
    else:
        if x+steps[y][x] < dx: 
            find_min_jumps(x+steps[y][x], y, c + 1, w + f'x{steps[y][x]}')
        if y+steps[y][x] < dy:
            find_min_jumps(x, y+steps[y][x], c + 1, w + 'y' + str(steps[y][x]))


lab = get_tpl('lab.txt') # входные данные
# находи количество элементов в строке, это будет ширина лабиринта и находим количество строк, это будет длина лабиринт
rx, ry = len(lab[0]), len(lab)
price_lst = [0, '']
steps = get_tpl('ways.txt')
resTwo = [len(steps[0])**2, ""]
dx, dy = len(steps[0]), len(steps)
find_min_jumps(0,0,0, "")
FindMaxWay(0,0, lab[0][0], '')
print("Максимальноая ценая за прохождение {0}, путь {1}".format(price_lst[0], price_lst[1]))
print ("\nМинимальное кол-во шагов: {0}, Путь: {1}".format(resTwo[0], resTwo[1]))
'''
