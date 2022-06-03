### `http://162.55.220.72:5005/first`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.
```
pm.test("Body matches string", function () {
  pm.expect(pm.response.text()).to.include("This is the first responce from server!");
});
```
### `http://162.55.220.72:5005/user_info_3`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let jsonData = pm.response.json ()
```
4. Проверить, что name в ответе равно name s request (name вбить руками.)
```
pm.test("Name = Alona", function () {
    pm.expect(jsonData.name).to.eql("Alona");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)
```
pm.test("Age = 25", function () {
    pm.expect(jsonData.age).to.eql("25");
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```
pm.test("Salary = 1000", function () {
    pm.expect(jsonData.salary).to.eql(1000);
});
```
7. Спарсить request.
```
let reqData = request.data
```
8. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Name = BodyName", function () {
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("Age = BodyAge", function () {
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
let salaryInt = parseInt(reqData.salary)

pm.test("Salary = BodySalary", function () {
    pm.expect(jsonData.salary).to.eql(salaryInt);
});

```
11. Вывести в консоль параметр family из response.
```
console.log(jsonData.family);
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```
pm.test("u_salary_1_5_year", function () {
    pm.expect(jsonData.family.u_salary_1_5_year).to.eql(salaryInt*4);
});
```

### `http://162.55.220.72:5005/object_info_3`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let jsonData = pm.response.json ()
```
4. Спарсить request.
```
let reqData = pm.request.url.query.toObject ();
let salaryInt = parseInt(reqData.salary)
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Name = ParamsName", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("Age = ParamsAge", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("Salary = ParamsSalary", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary).to.eql(salaryInt);
});
```
8. Вывести в консоль параметр family из response.
```
console.log(respData.family);
```
9. Проверить, что у параметра dog есть параметры name.
```
pm.test("Dog has a name", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog).to.have.property("name");
});
```
10. Проверить, что у параметра dog есть параметры age.
```
pm.test("Dog has an age", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog).to.have.property("age");
});
```
11. Проверить, что параметр name имеет значение Luky.
```
pm.test("Dog has name Luky", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog.name).to.eql("Luky");
});
```
12. Проверить, что параметр age имеет значение 4.
```
pm.test("Dog has age 4", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog.age).to.eql(4);
});
```

### `http://162.55.220.72:5005/object_info_4`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let jsonData = pm.response.json;
```
4. Спарсить request.
```
let reqData = pm.request.url.query.toObject();
let salaryInt = parseInt(reqData.salary);
let ageInt = parseInt(reqData.age);
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Name = ParmsName", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
6. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("Age = ParmsAge", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.age).to.eql(ageInt);
});
```
7. Вывести в консоль параметр salary из request.
```
console.log (salaryInt);
```
8. Вывести в консоль параметр salary из response.
```
console.log (jsonData.salary);
```
9. Вывести в консоль 0-й элемент параметра salary из response.
```
console.log (jsonData.salary[0]);
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```
console.log (jsonData.salary[1]);
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```
console.log (jsonData.salary[2]);
```
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```
pm.test("Salary_0_req", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary[0]).to.eql(salaryInt);
});
```
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```
pm.test("Salary_1_req", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary[1]).to.eql+(reqData.salary * 2);
});
```
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```
pm.test("Salary_2_req", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary[2]).to.eql+(reqData.salary * 3);
});
```
15. Создать в окружении переменную name
16. Создать в окружении переменную age
17. Создать в окружении переменную salary
18. Передать в окружение переменную name
```
pm.environment.set("name", jsonData.name);
```
19. Передать в окружение переменную age
```
pm.environment.set("age", jsonData.age);
```
20. Передать в окружение переменную salary
```
pm.environment.set("salary", jsonData.salary[0]);
```

21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```
for (let i of jsonData.salary) {
    console.log(i);
}
```

### `http://162.55.220.72:5005/user_info_2`
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос.
5. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
6. Спарсить response body в json.
```
let jsonData = pm.response.json();
```
7. Спарсить request.
```
let reqData = request.data;
```
8. Проверить, что json response имеет параметр start_qa_salary
```
pm.test("response_has_start_qa_salary", function () {
    pm.expect(jsonData).to.have.property("start_qa_salary");
});

```
9. Проверить, что json response имеет параметр qa_salary_after_6_months
```
pm.test("response_has_qa_salary_after_6_months"), function() {
    pm.expect(jsonData).to.have.property("qa_salary_after_6_months")
};
```
10. Проверить, что json response имеет параметр qa_salary_after_12_months
```
pm.test ("response_has_qa_salary_after_12_months"), function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_12_months")
};
```
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```
pm.test ("response_has_qa_salary_after_1.5_year"), function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_1.5_year")
};
```
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```
pm.test ("response_has_qa_salary_after_3.5_years"), function () {
    pm.expect(jsonData).to.have.property("qa_salary_after_3.5_years")
};
```
13. Проверить, что json response имеет параметр person
```
pm.test ("response_has_person"), function () {
    pm.expect(jsonData).to.have.property("person")
};
```
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```
let salaryInt = parseInt(reqData.salary)

pm.test("start_qa_salary=salary", function () {
    pm.expect(jsonData.start_qa_salary).to.eql(salaryInt);
});
```
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```
pm.test("qa_salary_after_6_months=salary*2", function () {
    pm.expect(jsonData.qa_salary_after_6_months).to.eql(salaryInt*2);
});
```
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```
pm.test("qa_salary_after_12_months=salary*2.7", function () {
    pm.expect(jsonData.qa_salary_after_12_months).to.eql(salaryInt*2.7);
});
```
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```
pm.test("qa_salary_after_1.5_year=salary*3.3", function () {
    pm.expect(jsonData["qa_salary_after_1.5_year"]).to.eql(salaryInt*3.3);
});
```
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```
pm.test("qa_salary_after_3.5_years=salary*3.8", function () {
   pm.expect(jsonData["qa_salary_after_3.5_years"]).to.eql(salaryInt*3.8);
});
```
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```
pm.test("u_name1=salary", function () {
   pm.expect(jsonData.person.u_name[1]).to.eql(salaryInt);
});
```
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```
pm.test("u_age=age", function () {
   pm.expect(jsonData.person.u_age).to.eql(+reqData.age);
});
```
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```
pm.test("u_salary_5_years=salary*4.2", function () {
   pm.expect(jsonData.person.u_salary_5_years).to.eql(salaryInt*4.2);
});
```
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```
for(let DATA in jsonData.person) {
   if(typeof(jsonData.person[DATA]) == "object"){
       for(let i = 0; i < Object.keys(jsonData.person[DATA]).length; i++){
           console.log(jsonData.person[DATA][i]);
       }
   }
else {console.log(jsonData.person[DATA])}
}

```
