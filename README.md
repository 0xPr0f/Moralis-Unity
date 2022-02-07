# Moralis-Unity

This is moralis unity web3api query where we call different api menthods with one line of code.     

code summary :
```cs

    public async void GetNFT()
    {
        OutPutAddress.text = "Fetching your NFTs...";
        NftOwnerCollection balance = await MoralisInterface.GetClient().Web3Api.Account.GetNFTs(AddressText.text.ToLower(), ChainList.mumbai);
        string NFTbalance = balance.ToJson();
        OutPutAddress.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);

    }

    public async void NFTInContractfromAdd()
    {
        OutPutAddress.text = "Fetching your NFTs from " + TokenText.text + "...";
        NftOwnerCollection balance = await MoralisInterface.GetClient().Web3Api.Account.GetNFTsForContract(AddressText.text.ToLower(), TokenText.text, ChainList.mumbai);
        string NFTbalance = balance.ToJson();
        OutPutAddress.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);
    }

    public async void TokenBalance()
    {
        OutPutAddress.text = "Fetching your ERC 20 Token balances...";
        List<Erc20TokenBalance> balance = await MoralisInterface.GetClient().Web3Api.Account.GetTokenBalances(AddressText.text.ToLower(), ChainList.eth);
        OutPutAddress.text = "";
        for (int i = 0; i < balance.Count; i++)
        {
            OutPutAddress.text += JToken.Parse(balance[i].ToJson()).ToString(Formatting.Indented);
        }

    }

    public async void TokenTransfers()
    {
        OutPutAddress.text = "Fetching your Token Trasactions..";
        Erc20TransactionCollection balance = await MoralisInterface.GetClient().Web3Api.Account.GetTokenTransfers(AddressText.text.ToLower(), ChainList.eth);
        string NFTbalance = balance.ToJson();
        OutPutAddress.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);
    }

   

    public async void AllNFTContract()
    {
        OutPutToken.text = "Fetching All metadata in " + TokenText.text;
        NftCollection nfts = await MoralisInterface.GetClient().Web3Api.Token.GetAllTokenIds(TokenText.text, ChainList.mumbai);
        string NFTbalance = nfts.ToJson();
        OutPutToken.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);
    }

    public async void NFTcontractTransfers()
    {
        OutPutToken.text = "Fetching All Contract transfers in " + TokenText.text;
        NftTransferCollection nftTransfers = await MoralisInterface.GetClient().Web3Api.Token.GetContractNFTTransfers(TokenText.text, ChainList.mumbai);
        string NFTbalance = nftTransfers.ToJson();
        OutPutToken.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);
    }
    public async void NFTmetadata()
    {
        OutPutToken.text = "Fetching All Contract metadata";
        NftContractMetadata metadata = await MoralisInterface.GetClient().Web3Api.Token.GetNFTMetadata(TokenText.text, ChainList.mumbai);
        string NFTbalance = metadata.ToJson();
        OutPutToken.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);
    }
    public async void Search()
    {
        OutPutToken.text = "Searching For NFT...";
        NftMetadataCollection metadata = await MoralisInterface.GetClient().Web3Api.Token.SearchNFTs(search.text, ChainList.eth, null, null, null, null, null, null, 0, 100);
        string NFTbalance = metadata.ToJson();
        OutPutToken.text = JToken.Parse(NFTbalance).ToString(Formatting.Indented);

    }
    ```
    
    Watch full video : https://youtu.be/daDiqU7UkHc