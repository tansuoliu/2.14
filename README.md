<情人节礼物>
import pygame
import random
import math

# 初始化Pygame
pygame.init()

# 设置屏幕大小
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("刘宇航 ❤ 李爽")

# 定义颜色
WHITE = (255, 255, 255)
PINK = (255, 192, 203)
RED = (255, 0, 0)

# 定义字体
font = pygame.font.Font(None, 36)

# 定义爱人名字
your_name = "刘宇航"
lover_name = "李爽"

# 检查名字
if your_name != "刘宇航" or lover_name != "李爽":
    print("名字错误，程序无法运行。")
    exit()

# 定义树的生长参数
tree_growth = 0
max_tree_growth = 100

# 定义心的跳动参数
hearts = []

# 定义相识日期
meet_date = "2023年3月9号"

# 绘制树
def draw_tree(x, y, growth):
    trunk_width = 10 + growth * 0.2
    trunk_height = 50 + growth * 2
    leaves_radius = 30 + growth * 1.5

    # 绘制树干
    pygame.draw.rect(screen, (139, 69, 19), (x - trunk_width / 2, y - trunk_height, trunk_width, trunk_height))

    # 绘制树叶
    pygame.draw.circle(screen, PINK, (x, y - trunk_height - int(leaves_radius / 2)), leaves_radius)

# 绘制心
def draw_heart(x, y, size):
    pygame.draw.polygon(screen, RED, [
        (x, y - size),
        (x - size, y),
        (x, y + size),
        (x + size, y)
    ])

# 主循环
running = True
clock = pygame.time.Clock()

while running:
    screen.fill(WHITE)

    # 处理事件
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # 绘制树
    draw_tree(screen_width // 2, screen_height - 50, tree_growth)

    # 树的生长
    if tree_growth < max_tree_growth:
        tree_growth += 0.1

    # 绘制跳动的心
    if random.random() < 0.1:
        heart_x = random.randint(0, screen_width)
        heart_y = random.randint(0, screen_height)
        hearts.append((heart_x, heart_y, 0))

    for i, (x, y, size) in enumerate(hearts):
        if size < 20:
            hearts[i] = (x, y, size + 0.5)
        else:
            hearts.pop(i)
        draw_heart(x, y, size)

    # 绘制文字
    text = font.render(f"{your_name} ❤ {lover_name}", True, RED)
    screen.blit(text, (screen_width // 2 - text.get_width() // 2, 50))

    text = font.render(f"相识相知相爱至今: {meet_date}", True, RED)
    screen.blit(text, (screen_width // 2 - text.get_width() // 2, 100))

    # 更新屏幕
    pygame.display.flip()
    clock.tick(60)

pygame.quit()
