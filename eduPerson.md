# 小测 eduPerson智能合约

# 一, 合约编写
1, eduPersonStorage
```
pragma solidity ^0.4.25;

contract eduPersonStorage {
    
    struct Person {
        string Id;               // 0 id
        string Account;          // 1 账户
        bytes32 Password;        // 2 密码
        string Phone;            // 3 电话
        string Email;            // 4 邮箱
        string Name;             // 5 姓名
        string Address;          // 6 地址
        string College;          // 7 学院
        string Department;       // 8 系别
        string Class;            // 9 班级
        string Type;             //10 类型
        bool isVaild;
    }
    
    // accountMap[_type][_account]
    mapping(string => mapping(string => Person)) accountMap;
    
    mapping(string => Person) id2PersonMap;
    
    
    
    // 1, 注册
    function _insertPerson (
        string _id,
        string _account,
        string _password,
        string _phone,
        string _email,
        string _name,
        string _address,
        string _college,
        string _department,
        string _class,
        string _type
     )  internal {
        Person storage p = accountMap[_type][_account];
        p.Id = _id;
        p.Account = _account;
        p.Password = keccak256(abi.encodePacked(_password));
        p.Phone = _phone;
        p.Type = _type;
        p.Email = _email;
        p.Name = _name;
        p.Address = _address;
        p.College = _college;
        p.Department = _department;
        p.Class = _class;
        p.Type = _type;
        accountMap[_type][_account].isVaild = true;
        id2PersonMap[p.Id] = p;
    }
    
    // 判断用户是否存在
    function userExists(string _type, string _account) internal view returns(bool) {
        if (accountMap[_type][_account].isVaild) {
            return true;
        } 
            return false;
    }
    
    
    // 判断用户id是否存在
    function userIdExists(string _id) internal view returns(bool) {
        if(id2PersonMap[_id].isVaild){
            return true;
        }
            return false;
    }

        
  }
```

2, eduPerson
```
pragma experimental ABIEncoderV2;

import { eduPersonStorage } from "./eduPersonStorage.sol";

contract eduPerson is eduPersonStorage {
    
    // 新增用户
    function newPeople(string[] memory PersonDatas) {
        // 判断用户是否存在
        require(!userExists(PersonDatas[10],PersonDatas[1]), "user exists!");
        // 判断id是否存在
        require(!userIdExists(PersonDatas[0]), "id exists!");
        _insertPerson(
            PersonDatas[0],         
            PersonDatas[1],         
            PersonDatas[2],
            PersonDatas[3],
            PersonDatas[4],
            PersonDatas[5],
            PersonDatas[6],
            PersonDatas[7],
            PersonDatas[8],
            PersonDatas[9],
            PersonDatas[10]
        );
    }
    
    // 新增老师
    function newTeacher(string[] memory TeracherDatas) {
        // 判断用户是否存在
        require(!userExists("teacher",TeracherDatas[1]), "teacher exists!");
        // 判断id是否存在
        require(!userIdExists(TeracherDatas[0]), "id exists!");
        _insertPerson(
            TeracherDatas[0],         
            TeracherDatas[1],         
            TeracherDatas[2],
            TeracherDatas[3],
            TeracherDatas[4],
            TeracherDatas[5],
            TeracherDatas[6],
            TeracherDatas[7],
            TeracherDatas[8],
            TeracherDatas[9],
            "teacher"
        );
      }
      
      
      // 新增工作人员
    function newShcool(string[] memory SchoolDatas) {
        // 判断用户是否存在
        require(!userExists("school",SchoolDatas[1]), "school exists!");
        // 判断id是否存在
        require(!userIdExists(SchoolDatas[0]), "id exists!");
        _insertPerson(
            SchoolDatas[0],         
            SchoolDatas[1],         
            SchoolDatas[2],
            SchoolDatas[3],
            SchoolDatas[4],
            SchoolDatas[5],
            SchoolDatas[6],
            SchoolDatas[7],
            SchoolDatas[8],
            SchoolDatas[9],
            "school"
        );
      }
    
    
    
    
    
   // 登录
    function login(string memory _type, string memory _account, string memory _password) public view returns (Person) {
        require(userExists(_type,_account),"user no found.");
        // 因为前面新增的时候密码已经加密过了 所以这里不用再次加密对比 只需把入参_password加密
        require(accountMap[_type][_account].Password == keccak256(_password),"password is no right");
        Person p = accountMap[_type][_account];
        // 返回用户前端判断登录角色
        return p;
    }
    
  }
```

# 二, 测试用例

# 1, 测试参数
```
学生注册Param : ["1","2624134616","123456","15314908141","2624@qq.com","fb","sz","rgzn","blockchain","2","student"]
学生登录Param : ["student","2624134616","123456"]

老师注册Param : ["2","13878","123456","13534006689","2628@qq.com","zs","sz","rgzn","blockchain","2"]
老师登录Param : ["teacher",[13878],"123456"]

工作人员注册Param : ["3","13666","123456","1353698789","2622@qq.com","zs","sz","rgzn","blockchain","2"]
工作人员登录Param : ["13666","123456"]
```
# 2,用户测试结果

![image](https://user-images.githubusercontent.com/103564714/164889199-f8b5b42b-c877-40c0-9c48-2c8028fbc50b.png)
![image](https://user-images.githubusercontent.com/103564714/164889206-2e2cd1b7-b9c1-404a-bf73-c93f62438a39.png)
![image](https://user-images.githubusercontent.com/103564714/164889222-405200b6-09dd-4a9f-b9c3-fbda890ac6b2.png)
![image](https://user-images.githubusercontent.com/103564714/164901902-ac41ca63-9763-4376-866b-c8af43c53e8e.png)


# ------------------------------------------------------------------------------
# 2.1 密码错误测试

![image](https://user-images.githubusercontent.com/103564714/164889258-8501f431-d1be-40b5-8060-949a3d781851.png)
![image](https://user-images.githubusercontent.com/103564714/164889276-81d440f0-0b31-4a8d-b44d-7d993af659f1.png)

# ------------------------------------------------------------------------------
# 3,老师测试结果


![image](https://user-images.githubusercontent.com/103564714/164889471-5a860434-8953-4c49-b140-8a7b81215d9a.png)
![image](https://user-images.githubusercontent.com/103564714/164889474-a874f3a6-a5ae-4948-8f80-0d91b87dff19.png)
![image](https://user-images.githubusercontent.com/103564714/164889480-f21a9983-f359-4e1b-ad31-498f23b38fca.png)
![image](https://user-images.githubusercontent.com/103564714/164903640-80c63e51-e27c-42da-b414-2a0de7f343d0.png)


# ------------------------------------------------------------------------------
# 3.1 密码错误测试

![image](https://user-images.githubusercontent.com/103564714/164889488-1eb446e8-0316-4fd1-84f9-54035f76c217.png)
![image](https://user-images.githubusercontent.com/103564714/164889491-159004ee-d397-443e-bcc7-1a3454cebe83.png)

# 工作人员和老师测试结果一致 这里就不测试了~












