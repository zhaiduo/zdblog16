---
title: More about PHP开发
id: 2123
categories:
  - 杂项
tags:
---

Design:
Domain-Driven Design
领域驱动设计(Domain Driven Design)是一种软件开发方法，目的是让软件系统在实现时准确的基于对真实业务过程的建模并根据真实业务过程的调整而调整。

领域驱动设计没有开始和结束——它是一个不断的再评估，再重构，再建模，再设计的持续过程——每一次的对话都会使你对问题有更进一步的理解。

Behaviour-Driven Development

Test:
Test-Driven Development (or simply TDD).
**Gherkin** is very structural makes it very easy to automate and autotest your behaviour examples against a developing application.

Feature: Product basket
  In order to buy products
  As a customer
  I need to be able to put interesting products into a basket
This is a basic Gherkin feature and it is a simple description of this feature’s story. Every feature starts with this same format: a line with the title of the feature, followed by three lines that describe the benefit, the role and the feature itself with any amount of additional description lines following after.

Cucumber
beHat

Package：
Composer is a package manager for PHP

Refactoring

Inversion of Control, or IoC, is a technique that allows control to be inverted when compared to classical procedural code. The most prominent form of IoC is, of course, Dependency Injection, or DI. Laravel's IoC container is one of the most used Laravel features, yet is probably the least understood.

Queue

The queue configuration file is stored in app/config/queue.php. In this file you will find connection configurations for each of the queue drivers that are included with the framework, which includes a Beanstalkd, IronMQ, Amazon SQS, Redis, and synchronous (for local use) driver.

The following dependencies are needed for the listed queue drivers:

Beanstalkd: pda/pheanstalk ~2.0
Amazon SQS: aws/aws-sdk-php
IronMQ: iron-io/iron_mq

Artisan is the name of the command-line interface included with Laravel. It provides a number of helpful commands for your use while developing your application. It is driven by the powerful Symfony Console component.

object-relational-mapping library [ORM] ?