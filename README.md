import pygame
import random
import pymunk
import numpy as np

# Initialize Pygame
pygame.init()

# Screen settings
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("AI Bike Game with Dynamic Weather")

# Colors
WHITE = (255, 255, 255)
GRAY = (100, 100, 100)
BLUE = (50, 50, 255)

# Physics setup
space = pymunk.Space()
space.gravity = (0, 900)  # Gravity

# Bike class
class Bike:
    def __init__(self, x, y):
        self.body = pymunk.Body(1, pymunk.moment_for_box(1, (50, 20)))
        self.body.position = x, y
        self.shape = pymunk.Poly.create_box(self.body, (50, 20))
        self.shape.color = (255, 0, 0, 255)
        space.add(self.body, self.shape)

    def move(self, direction):
        force = 5000 if direction == "right" else -5000
        self.body.apply_force_at_local_point((force, 0), (0, 0))

# Weather AI (Uses random & noise for smooth transitions)
class Weather:
    def __init__(self):
        self.clouds = [random.randint(0, WIDTH) for _ in range(5)]
        self.rain_intensity = 0
    
    def update(self):
        self.rain_intensity = int(50 * (np.sin(pygame.time.get_ticks() * 0.0001) + 1))
        for i in range(len(self.clouds)):
            self.clouds[i] += random.randint(-1, 1)  # Cloud movement
            
    def draw(self, screen):
        for x in self.clouds:
            pygame.draw.circle(screen, GRAY, (x, 100), 40)
        for _ in range(self.rain_intensity):
            pygame.draw.line(screen, BLUE, (random.randint(0, WIDTH), random.randint(0, HEIGHT)), (random.randint(0, WIDTH), HEIGHT), 1)

# Game loop
bike = Bike(400, 300)
weather = Weather()
clock = pygame.time.Clock()

running = True
while running:
    screen.fill(WHITE)
    
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    keys = pygame.key.get_pressed()
    if keys[pygame.K_RIGHT]: bike.move("right")
    if keys[pygame.K_LEFT]: bike.move("left")
    
    # Update physics and weather
    space.step(1/50)
    weather.update()
    
    # Draw elements
    weather.draw(screen)
    pygame.draw.rect(screen, (255, 0, 0), (int(bike.body.position.x), int(bike.body.position.y), 50, 20))

    pygame.display.flip()
    clock.tick(60)

pygame.quit()
