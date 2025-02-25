from panda3d.core import WindowProperties, LVector3
from direct.showbase.ShowBase import ShowBase
from direct.task import Task
import random

class BattleRoyale(ShowBase):
    def __init__(self):
        super().__init__()

        # Window settings
        wp = WindowProperties()
        wp.setSize(1280, 720)
        self.win.requestProperties(wp)

        # Load environment
        self.scene = self.loader.loadModel("models/environment")
        self.scene.reparentTo(self.render)
        self.scene.setScale(0.25, 0.25, 0.25)
        self.scene.setPos(-8, 42, 0)

        # Load Player
        self.player = self.loader.loadModel("models/panda")
        self.player.reparentTo(self.render)
        self.player.setScale(0.005, 0.005, 0.005)
        self.player.setPos(0, 10, 0)

        # Camera follows player
        self.taskMgr.add(self.update_camera, "update_camera")

    def update_camera(self, task):
        self.camera.setPos(self.player.getX(), self.player.getY() - 10, 2)
        self.camera.lookAt(self.player)
        return Task.cont

game = BattleRoyale()
game.run()
