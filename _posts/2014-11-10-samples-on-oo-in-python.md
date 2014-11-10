---
layout: post
title: "Samples on OO in Python"
description: ""
category: 
tags: []
---
{% include JB/setup %}

#Binding a function to an class instance
	class test:
		def __init__(self, name):
			self.name = name
	def fun1():
		print self.name
	def fun2(self):
		print self.name
	def fun3(a):
		print a.name
	t = test("myname")

	t.p = fun1() #Error: global name 'self' is not defined

	t.p = fun1 
	t.p() #Error: global name 'self' is not defined

	t.p = fun1.__get__(t,p) # Error: name 'p' is not defined

	t.p = fun1.__get__(t, fun1) 
	t.p() # Error: fun() takes no arguments (1 given)
	
	t.p = fun2.__get__(t, fun2)
	t.p = fun3.__get__(t, fun3)
	# both work
