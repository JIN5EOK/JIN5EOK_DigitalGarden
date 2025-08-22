---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/DotNet 객체의 세대/","noteIcon":"","updated":"2025-07-19T22:58:36.000+09:00"}
---

> 객체가 **GC수집 검사**로부터 **얼마나 오래 생존**했는지를 세대로 구분한다

* **GC수집 검사**
	* 각 검사마다 세대를 **1세대씩 증가**, **최대 2세대**까지 증가시킨다
	* **세대가 올라갈수록** 검사 **빈도를 낮춘다**

* **0~2세대**
	* 🥚 0세대 👶
		* GC수집 사이클 **한번만에** 검사
	* 🐥 1세대 👨
		* GC수집 사이클 **10회당 한번** 검사
	* 🐓 2세대 👴
		* GC수집 사이클 **100회당 한번** 검사


[[02.DevWiki/Sources/DotNet Garbage Collection (닷넷 가비지컬렉션)\|DotNet Garbage Collection (닷넷 가비지컬렉션)]]