#!/usr/bin/env python
# coding:utf-8

import os
import eyed3


class Mp3Genre(object):
    """
    方便自己修改mp3文件的流派
    2014-02-14
    """
    
    def __init__(self, path):
        self.path = path
        self.mp3_list = []
        self.fun()
    
    def fun(self):
        """
        将查找到的mp3添加到列表
        """
        for root, dirs, files in os.walk(self.path):
            dirs[:] = []
            for fn in files:
                mp3_path = root + "\\" + fn
                ext = os.path.splitext(mp3_path)[1]
                if ext in (".MP3", ".mp3"):
                    self.mp3_list.append(mp3_path)
                    
    def todo(self, genre):
        """
        导入eyed3修改mp3流派
        """
        if self.mp3_list:
            for mp3_path in self.mp3_list:
                load_file = eyed3.load(mp3_path)
                load_file.tag._setGenre(genre)
                load_file.tag.save(encoding="utf8")
            print u"处理完毕"
        else:
            print u"找不到mp3后缀的歌曲"
 
 
if __name__ == "__main__":
    mp3_genre = Mp3Genre(r"D:\MyMusic")
    mp3_genre.todo(u"摇滚")
