# ... existing code ...

def draw_snake(snake_block, snake_list):
    # 绘制蛇身
    for i, x in enumerate(snake_list[:-1]):  # 除了头部的身体部分
        # 创建渐变色效果
        color_value = max(50, 255 - (i * 10))  # 越往后的身体部分颜色越深
        snake_color = (0, color_value, 0)  # 绿色渐变
        pygame.draw.rect(game_window, snake_color, [x[0], x[1], snake_block, snake_block])
    
    # 绘制蛇头
    head = snake_list[-1]
    pygame.draw.rect(game_window, green, [head[0], head[1], snake_block, snake_block])
    
    # 添加眼睛
    eye_radius = 2
    if x1_change > 0:  # 向右看
        pygame.draw.circle(game_window, black, (int(head[0] + snake_block - 2), int(head[1] + 3)), eye_radius)
    elif x1_change < 0:  # 向左看
        pygame.draw.circle(game_window, black, (int(head[0] + 2), int(head[1] + 3)), eye_radius)
    elif y1_change < 0:  # 向上看
        pygame.draw.circle(game_window, black, (int(head[0] + snake_block/2), int(head[1] + 2)), eye_radius)
    else:  # 向下看
        pygame.draw.circle(game_window, black, (int(head[0] + snake_block/2), int(head[1] + snake_block - 2)), eye_radius)
    
    # 添加舌头
    tongue_color = (213, 50, 80)  # 红色舌头
    if x1_change > 0:  # 向右
        pygame.draw.line(game_window, tongue_color, (head[0] + snake_block, head[1] + snake_block/2), 
                        (head[0] + snake_block + 5, head[1] + snake_block/2), 2)
    elif x1_change < 0:  # 向左
        pygame.draw.line(game_window, tongue_color, (head[0], head[1] + snake_block/2), 
                        (head[0] - 5, head[1] + snake_block/2), 2)
    elif y1_change < 0:  # 向上
        pygame.draw.line(game_window, tongue_color, (head[0] + snake_block/2, head[1]), 
                        (head[0] + snake_block/2, head[1] - 5), 2)
    else:  # 向下
        pygame.draw.line(game_window, tongue_color, (head[0] + snake_block/2, head[1] + snake_block), 
                        (head[0] + snake_block/2, head[1] + snake_block + 5), 2)

# ... existing code ...
