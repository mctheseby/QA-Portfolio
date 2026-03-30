# 🐞 Bug Report: HTML-разметка рекомендаций отображается как обычный текст

## 📋 Основная информация
- **Проект:** SberStart QA
- **URL:** https://sberstudent.ru/sberstart-qa/
- **Компонент:** Результат квиза (GameResult)
- **Тип бага:** Frontend, React

## 🚨 Severity: Medium
## 🎯 Priority: Medium/High

## 🔍 Шаги воспроизведения
1. Перейти на https://sberstudent.ru/sberstart-qa/
2. Пройти квиз по тестированию
3. Получить результат "Новичок"
4. Обратить внимание на блок "Рекомендуем ознакомиться с материалами"

## ❌ Фактический результат
HTML-теги отображаются как текст, ссылки не кликабельны

## ✅ Ожидаемый результат
HTML-разметка интерпретируется браузером, ссылки кликабельны

## 🔧 Причина
React-компонент передаёт HTML-строку как text children:
`n.createElement("p", null, h[s].recommendation)`

## 🛠 Исправление
`n.createElement("p", { dangerouslySetInnerHTML: { __html: recommendation } })`

## 📊 Статус: OPEN
