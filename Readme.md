Token name

    string private _name = "MyToken";

Token symbol

    string private _symbol = "MTK";

Initial supply

    uint256 private _initialSupply = 1000000 * 10**decimals();

Constructor to initialize the token with the initial supply

    constructor() ERC20(_name, _symbol) {
        _mint(msg.sender, _initialSupply);
    }

Modifier to ensure that only the contract owner can call a function

    modifier onlyOwner() {
        require(msg.sender == owner(), "Caller is not the owner");
        _;
    }

Function to allow the contract owner to mint new tokens

    function mint(address account, uint256 amount) external onlyOwner {
        _mint(account, amount);
    }

Function to allow any user to transfer tokens

    function transferTokens(address to, uint256 amount) external {
        _transfer(msg.sender, to, amount);
    }

Function to allow any user to burn their own tokens

    function burnTokens(uint256 amount) external {
        _burn(msg.sender, amount);
    }

