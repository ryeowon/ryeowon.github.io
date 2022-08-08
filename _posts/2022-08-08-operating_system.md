---
title: "운영체제(Operating System)란?"
date: 2022-08-08 00:00:00
categories: [OS]
tags: [operating system] # TAG names should always be lowercase
---

[Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/){:target="\_blank"}를 읽고 정리한 글입니다.

## 운영체제란?

쉽게 말하면 운영체제(Operating System, OS)는 **컴퓨터 프로그램이 잘 실행되도록 관리하는 소프트웨어**이다.  
OS는 다음과 같은 역할을 한다.

- 프로그램을 쉽게 실행할 수 있게 하며, 우리 눈에 여러 프로그램이 동시에 실행되는 것처럼 보이게 한다.
- 여러 프로그램이 메모리를 공유하여 사용하도록 메모리를 관리한다.
- 프로그램이 마우스, 키보드와 같은 장치들과 상호작용하게 한다.
- 시스템이 정확하고 효율적이게 동작하고, **사용하게 쉽게** 만든다.

윈도우, 리눅스와 같은 것들이 운영체제의 예이다.

## Virtualization

운영체제의 주요 역할은 **가상화(Virtualization)**이다.  
CPU, 메모리, 디스크와 같은 **물리적 자원을 가상화하여 더 사용하기 쉽게** 만드는데, 그래서 운영체제를 **virtual machine**이라고 부르기도 한다.

## Resource Manager

많은 프로그램이 동시에 실행되면 프로그램들은 **CPU와 메모리, 디스크 등을 공유하여 사용**한다. CPU, 메모리, 디스크는 시스템의 자원들이며 이것을 관리하는 OS는 **resource manager**이라고도 불린다.  
운영체제는 이러한 자원들을 효율적으로 관리하고, 어떤 한 프로그램에 치중되지 않고 공평하게 사용될 수 있도록 한다.

## Standard Library

OS는 사용자에게 할 일을 지시받는다. 사용자를 위해 OS는 많은 **인터페이스를 제공**하여 파일 접근, 프로그램 실행 등을 지시할 수 있도록 한다. 어플리케이션을 사용할 수 있도록 OS는 몇백 개의 system calls를 제공하고 있고, 따라서 OS는 어플리케이션에 standard library를 제공한다고 말하기도 한다.

## Design Goals

- 시스템을 편리하게 만들기 위하여 **abstraction**(추상화)하기
  - abstraction은 쉽게 말해 복잡한 것을 간추리는 것
- **성능을 높이고**, overhead(extra instruction time, extra memory space 등)를 줄이는 것
- 어플리케이션 간의, 또는 어플리케이션과 OS간의 **protection** ( isolating processes )
  - 프로그램에서 발생한 오류가 다른 프로그램에 영향을 주지 않아야 함
- **신뢰성(reliability)**
  - OS는 멈추지 않아야 함. OS가 멈추면 모든 어플리케이션이 멈추게 됨
- energy-efficiency, security, mobility 등

<br/>
> reference: <https://pages.cs.wisc.edu/~remzi/OSTEP/intro.pdf>{:target="\_blank"}
