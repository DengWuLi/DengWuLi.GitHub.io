---
title: "BUPT JAVA: 群体对象_TreeMap"
index_img: /img/BUPT.png
banner_img: /img/Java.png
date: 2023-05-22
tags:
  - Java
category:
  - BUPT_JAVA
---

# 群体对象\_TreeMap

## 题目描述:

定义下述 5 个类 (这 5 个类与前边的作业的要求一致, 可以直接拿来用)
其中`SalariedEmployee`, `HourlyEmployee`, `CommissionEmployee` 继承自 `Employee`, `basePlusCommissionEmployee` 继承自 `CommissionEmployee`.
类属性如下:

```java
Employee: firstName,lastName,socialSecurityNumber
SalariedEmployee: weeklySalary // 周薪
HourlyEmployee: wage // 每周工钱
                hours //月工作小时数
CommissionEmployee: grossSales // 销售额
                   commissionRate // 提成比率
basePlusCommissionEmployee: baseSalary // 月基本工资
```

`Employee` 类中定义了抽象方法 `earning`, 用于计算员工的月工资
不同类中工资的计算方式:
| 类名 | 计算方式 |
| :--------------------------- | :------------------------------------- |
| `SalariedEmployee` | `weeklySalary * 4` |
| `HourlyEmployee` | `wage * hours` |
| `CommissionEmployee` | `grossSales * commissionRate` |
| `basePlusCommissionEmployee` | `grossSales*commissionRate+baseSalary` |

类还应该包括构造方法, `toString` 方法, 属性的 `get/set` 方法.
`firstName`, `lastName`, `socialSecurityNumber` 的初始化在构造方法中完成. 其中对 `firstName`, `lastName` 也要提供 `get/set` 方法, 对 `socialSecurityNumber` 只提供 `get` 方法.
其他属性要提供 `get/set` 方法

定义 `EmployeeException` 类, 该类继承自 `Exception`, 至少包含 `code` 和 `message` 两个属性, 分别代表错误码和错误信息.

定义类 `Factory`, 该类有私有属性 `employees`, 类型为 `TreeMap`.
完成下述功能 (将原题目的文字描述变成了表格描述, 语言表述略有化简):

| 定义的方法                                                | 作用                                                                            | 异常错误码和错误信息                              | 返回值                    |
| :-------------------------------------------------------- | :------------------------------------------------------------------------------ | :------------------------------------------------ | ------------------------- |
| `Employee getEmployee(String empSecNum)`                  | 用于查找并返回社会保险号为 `empSecNum` 的员工                                   | 错误码为 `1004`, 错误信息为 `employee not found.` | 根据返回的员工对象的引用. |
| `Employee deleteEmployee(String empSecNum)`               | 用于从 `TreeMap` 中删除社会保险号为 `empSecNum` 的员工                          | 错误码为 `1002`, 错误信息为 `employee not found.` | 返回该员工对象的引用      |
| `Employee addEmployee(Employee emp)`                      | 用于添加参数定义的员工对象到 `TreeMap`中                                        | 误码为 `1001`, 错误信息为 `employee exists.`      | 返回该员工对象的引用      |
| `Employee updateEmployee(String empSecNum, Employee emp)` | 用于更新员工集合中社会保险号为 `empSecNum` 的员工对象信息, 更新后的信息为 `emp` | 错误码为`1003`, 错误信息为 `employee not found.`  | 返回`emp`                 |
| `void printEmployees()`                                   | 用于输出每一个员工的信息                                                        | -                                                 | -                         |

用以上各类完成下述功能.

## 输入:

为若干行, 每行代表一个操作. 每行的格式为: 第一个字符串为操作命令, 其中:

| 命令     | 对应方法              |
| :------- | :-------------------- |
| `get`    | `getEmployee` 方法    |
| `add`    | `addEmployee` 方法    |
| `update` | `updateEmployee` 方法 |
| `delete` | `deleteEmployee` 方法 |
| `print`  | `printEmployees` 方法 |
| `exit`   | 表示程序结束          |

`add` 和 `update` 的后续格式为一个雇员的信息 (具体见样例):

输入个数如表所示, 紧跟着的三个字符串依次代表 `firstName`, `lastName`, `socialSecurityNumber`.
| Tag | 类名 | 数字意义 (按输入顺序标记的对应的意义) |
| :--- | :--------------------------- | :------------------------------------------- |
| `0` | `SalariedEmployee` | `weeklySalary` |
| `1` | `HourlyEmployee` | `wage`, `hours` |
| `2` | `CommissionEmployee` | `grossSales`, `commissionRate` |
| `3` | `basePlusCommissionEmployee` | `grossSales`, `commissionRate`, `baseSalary` |

`get` 和 `delete` 的后续格式为雇员的社会保险号 (具体见样例).
`print` 与 `exit` 没有后续输入。

## 输出:

`print` 操作, 依次输出 `TreeMap` 全部雇员信息 (格式见样例).
其他操作, 如果发生异常, 则输出错误代码和错误信息 (格式见样例), 否则, 输出对应方法返回的雇员信息 (格式见样例).

## 输入样例:

```txt
add 0 Ai Meng 2012673901 4312
add 1 NanXiong Qimu 2016782340 15.2 200
add 2 Guo Yang 2017672347 46781.3 0.1
add 3 Rong Huang 2018768901 7854.4 0.28 7098
get 2016782340
delete 2018768901
update 2 Guo Yang 2017672347 46780 0.1
get 2016782345
delete 20187890
print
exit
```

## 输出样例:

```txt
firstName:Ai; lastName:Meng; socialSecurityNumber:2012673901; earning:17248.00
firstName:NanXiong; lastName:Qimu; socialSecurityNumber:2016782340; earning:3040.00
firstName:Guo; lastName:Yang; socialSecurityNumber:2017672347; earning:4678.13
firstName:Rong; lastName:Huang; socialSecurityNumber:2018768901; earning:9297.23
firstName:NanXiong; lastName:Qimu; socialSecurityNumber:2016782340; earning:3040.00
firstName:Rong; lastName:Huang; socialSecurityNumber:2018768901; earning:9297.23
firstName:Guo; lastName:Yang; socialSecurityNumber:2017672347; earning:4678.00
1004
employee not found.
1002
employee not found.
firstName:Ai; lastName:Meng; socialSecurityNumber:2012673901; earning:17248.00
firstName:NanXiong; lastName:Qimu; socialSecurityNumber:2016782340; earning:3040.00
firstName:Guo; lastName:Yang; socialSecurityNumber:2017672347; earning:4678.00
```

## Java

```java
// 群体对象_TreeMap
// 2023/05/22
// 代码巨长

import java.util.Map;
import java.util.Scanner;
import java.util.TreeMap;

public class Main {
    public static void main(String[] args) throws EmployeeException {
        var input = new Scanner(System.in);
        String order;
        var factory = new Factory();
        while (true) {
            order = input.next();
            Employee employee = null;
            try {
                switch (order) {
                    case "exit" -> {
                        return;
                    }

                    case "add", "update" -> {
                        var tag = input.nextInt();

                        String firstName = input.next(), lastName = input.next(), socialSecurity = input.next();
                        switch (tag) {
                            case 0 -> {
                                employee = new SalariedEmployee(firstName, lastName, socialSecurity);
                                var weeklySalary = input.nextDouble();
                                ((SalariedEmployee) employee).setWeeklySalary(weeklySalary);
                            }
                            case 1 -> {
                                employee = new HourlyEmployee(firstName, lastName, socialSecurity);
                                double wage = input.nextDouble(), hours = input.nextDouble();
                                ((HourlyEmployee) employee).setWage(wage);
                                ((HourlyEmployee) employee).setHours(hours);
                            }
                            case 2 -> {
                                employee = new CommissionEmployee(firstName, lastName, socialSecurity);
                                double grossSales = input.nextDouble(), commissionRate = input.nextDouble();
                                ((CommissionEmployee) employee).setGrossSales(grossSales);
                                ((CommissionEmployee) employee).setCommissionRate(commissionRate);
                            }
                            case 3 -> {
                                employee = new basePlusCommissionEmployee(firstName, lastName, socialSecurity);
                                double grossSales = input.nextDouble(), commissionRate = input.nextDouble(), baseSalary = input.nextDouble();
                                ((basePlusCommissionEmployee) employee).setGrossSales(grossSales);
                                ((basePlusCommissionEmployee) employee).setCommissionRate(commissionRate);
                                ((basePlusCommissionEmployee) employee).setBaseSalary(baseSalary);
                            }
                        }
                        if (order.equals("add"))
                            employee = factory.addEmployee(employee);
                        else
                            employee = factory.updateEmployee(socialSecurity, employee);
                    }
                    case "get" -> employee = factory.getEmployee(input.next());
                    case "delete" -> employee = factory.deleteEmployee(input.next());
                    case "print" -> factory.printEmployees();
                }
                if (employee != null)
                    System.out.println(employee);

            } catch (EmployeeException e) {
                System.out.println(e.code);
                System.out.println(e.message);
            }
        }
    }
}

abstract class Employee implements Comparable<Employee> {
    private String firstName;
    private String lastName;
    private final String socialSecurity;

    public String getFirstName() {
        return firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public String getSocialSecurity() {
        return socialSecurity;
    }

    void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public Employee(String firstName, String lastName, String socialSecurity) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.socialSecurity = socialSecurity;
    }

    @Override
    public String toString() {
        return String.format("firstName:%s; lastName:%s; socialSecurityNumber:%s; earning:%.2f", firstName, lastName, socialSecurity, earning());
    }


    public int compareTo(Employee other) {
        return (int) (this.earning() - other.earning());
    }

    abstract double earning();
}


class SalariedEmployee extends Employee {
    private double weeklySalary;

    public double getWeeklySalary() {
        return weeklySalary;
    }

    public void setWeeklySalary(double weeklySalary) {
        this.weeklySalary = weeklySalary;
    }

    public SalariedEmployee(String firstName, String lastName, String socialSecurity) {
        super(firstName, lastName, socialSecurity);
    }

    public double earning() {
        return weeklySalary * 4;
    }

}

class HourlyEmployee extends Employee {
    public double getWage() {
        return wage;
    }

    public void setWage(double wage) {
        this.wage = wage;
    }

    public double getHours() {
        return hours;
    }

    public void setHours(double hours) {
        this.hours = hours;
    }

    private double wage;
    private double hours;

    public HourlyEmployee(String firstName, String lastName, String socialSecurity) {
        super(firstName, lastName, socialSecurity);
    }

    public double earning() {
        return wage * hours;
    }
}

class CommissionEmployee extends Employee {
    private double grossSales;
    private double commissionRate;

    public double getGrossSales() {
        return grossSales;
    }

    public void setGrossSales(double grossSales) {
        this.grossSales = grossSales;
    }

    public double getCommissionRate() {
        return commissionRate;
    }

    public void setCommissionRate(double commissionRate) {
        this.commissionRate = commissionRate;
    }

    public CommissionEmployee(String firstName, String lastName, String socialSecurity) {
        super(firstName, lastName, socialSecurity);
    }

    public double earning() {
        return grossSales * commissionRate;
    }
}

class basePlusCommissionEmployee extends CommissionEmployee {
    private double baseSalary;

    public double getBaseSalary() {
        return baseSalary;
    }

    public void setBaseSalary(double baseSalary) {
        this.baseSalary = baseSalary;
    }

    public basePlusCommissionEmployee(String firstName, String lastName, String socialSecurity) {
        super(firstName, lastName, socialSecurity);
    }

    public double earning() {
        return super.earning() + baseSalary;
    }
}

class EmployeeException extends Exception {
    public int code;
    public String message;

    EmployeeException(int code, String message) {
        this.code = code;
        this.message = message;
    }
}

class Factory {
    private final Map<String, Employee> employees = new TreeMap<>();

    public Employee getEmployee(String empSecNum) throws EmployeeException {
        if (employees.containsKey(empSecNum))
            return employees.get(empSecNum);
        else
            throw new EmployeeException(1004, "employee not found.");
    }

    public Employee deleteEmployee(String empSecNum) throws EmployeeException {
        if (employees.containsKey(empSecNum)) {
            var employee = employees.get(empSecNum);
            employees.remove(empSecNum);
            return employee;
        } else
            throw new EmployeeException(1002, "employee not found.");
    }

    public Employee addEmployee(Employee emp) throws EmployeeException {
        if (employees.containsKey(emp.getSocialSecurity()))
            throw new EmployeeException(1001, "employee exists.");
        else {
            employees.put(emp.getSocialSecurity(), emp);
            return emp;
        }
    }

    Employee updateEmployee(String empSecNum, Employee emp) throws EmployeeException {
        if (employees.containsKey(empSecNum)) {
            employees.put(empSecNum, emp);
            return employees.get(empSecNum);
        } else
            throw new EmployeeException(1003, "employee not found.");
    }

    public void printEmployees() {
        for (Map.Entry<String, Employee> entry : employees.entrySet()) {
            var value = entry.getValue();
            if (value != null)
                System.out.println(value);
        }
    }
}
```

<pre class="note note-info">
<strong>2023-05-22</strong> 
<strong>IP属地: 北京</strong>
</pre>
