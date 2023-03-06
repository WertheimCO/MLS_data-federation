//The following is an example code sample that demonstrates a basic implementation of this system:

pragma solidity ^0.8.0;

contract MultiLevelSecurity {
    
    mapping(address => bool) private admin;
    mapping(address => bool) private federation;
    mapping(address => bool) private user;
    
    struct Data {
        uint id;
        string name;
        string description;
    }
    
    mapping(uint => Data) private data;
    uint private dataCount;
    
    constructor() {
        admin[msg.sender] = true;
    }
    
    modifier onlyAdmin() {
        require(admin[msg.sender], "Only admin can access this function");
        _;
    }
    
    modifier onlyFederation() {
        require(federation[msg.sender], "Only federation can access this function");
        _;
    }
    
    modifier onlyUser() {
        require(user[msg.sender], "Only user can access this function");
        _;
    }
    
    function addAdmin(address _admin) public onlyAdmin {
        admin[_admin] = true;
    }
    
    function removeAdmin(address _admin) public onlyAdmin {
        admin[_admin] = false;
    }
    
    function addFederation(address _federation) public onlyAdmin {
        federation[_federation] = true;
    }
    
    function removeFederation(address _federation) public onlyAdmin {
        federation[_federation] = false;
    }
    
    function addUser(address _user) public onlyFederation {
        user[_user] = true;
    }
    
    function removeUser(address _user) public onlyFederation {
        user[_user] = false;
    }
    
    function addData(string memory _name, string memory _description) public onlyUser {
        dataCount++;
        data[dataCount] = Data(dataCount, _name, _description);
    }
    
    function getData(uint _id) public view onlyFederation returns (string memory, string memory) {
        return (data[_id].name, data[_id].description);
    }
    
}
