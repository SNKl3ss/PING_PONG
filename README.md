from pygame import *

class GameSprite(sprite.Sprite):
    def __init__(self, sp_image, sp_x, sp_y, size_x, size_y, hero_speed):
        super().__init__()
        self.picture = transform.scale(image.load(sp_image),(size_x, size_y))
        self.rect = self.picture.get_rect()
        self.rect.x = sp_x
        self.rect.y = sp_y
        self.speed = hero_speed

    def show(self):
        window.blit(self.picture,(self.rect.x, self.rect.y))

class Rocket(GameSprite):
    def update_right(self):
        keys_pressed = key.get_pressed()
        if keys_pressed[K_w] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys_pressed[K_s] and self.rect.y < win_height - 80:
            self.rect.y += self.speed

    def update_left(self):
        if keys_pressed[K_UP] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys_pressed[K_DOWN] and self.rect.y < win_height - 80:
            self.rect.y += self.speed
