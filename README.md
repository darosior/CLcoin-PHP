CLcoin-PHP
===============

A fork from [aceat64/EasyBitcoin-PHP](https://github.com/aceat64/EasyBitcoin-PHP), just adapted to the need of the CLcoin ( change prot, etc..). All I did was just replacing "Bitcoin" by "CLcoin". 
A simple class for making calls to CLcoin's API using PHP.

Getting Started
---------------
1. Include clcoin.php into your PHP script:

    ```php
    require_once('clcoin.php');
    ```
2. Initialize CLcoin connection/object:

    ```php
    $client = new CLcoin('username','password');
    ```

    Optionally, you can specify a host, port. Default is HTTP on localhost port 2332.

    ```php
    $client = new CLcoin('username','password','localhost','2332');
    ```

    If you wish to make an SSL connection you can set an optional CA certificate or leave blank
    ```php
    $client->setSSL('/full/path/to/mycertificate.cert');
    ````

3. Make calls to CLcoind as methods for your object. Examples:

    ```php
    $client->getinfo();
    
    $client->getrawtransaction('0e3e2357e806b6cdb1f70b54c3a3a17b6714ee1f0e68bebb44a74b1efd512098',1);
    
    $client->getblock('000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f');
    ```
    List of available methods :   
        addmultisigaddress <nrequired> <'["key","key"]'> [account]  
        addnode <node> <add|remove|onetry>  
        backupwallet <destination>  
        createmultisig <nrequired> <'["key","key"]'>  
        createrawtransaction [{"txid":txid,"vout":n},...] {address:amount,...}  
        decoderawtransaction <hex string>  
        dumpprivkey <CLcoinaddress>  
        encryptwallet <passphrase>  
        getaccount <CLcoinaddress>  
        getaccountaddress <account>  
        getaddednodeinfo <dns> [node]  
        getaddressesbyaccount <account>  
        getbalance [account] [minconf=1]  
        getbestblockhash  
        getblock <hash> [verbose=true]  
        getblockcount  
        getblockhash <index>  
        getblocktemplate [params]  
        getconnectioncount  
        getdifficulty  
        getgenerate  
        gethashespersec  
        getinfo  
        getmininginfo 
        getnetworkhashps [blocks] [height]  
        getnewaddress [account]  
        getnormalizedtxid <hex string>  
        getpeerinfo  
        getrawmempool  
        getrawtransaction <txid> [verbose=0]  
        getreceivedbyaccount <account> [minconf=1]  
        getreceivedbyaddress <CLcoinaddress> [minconf=1]  
        gettransaction <txid>  
        gettxout <txid> <n> [includemempool=true]  
        gettxoutsetinfo  
        getwork [data]  
        getworkex [data, coinbase]  
        help [command]  
        importprivkey <CLcoinprivkey> [label] [rescan=true]  
        keypoolrefill  
        listaccounts [minconf=1]  
        listaddressgroupings  
        listlockunspent  
        listreceivedbyaccount [minconf=1] [includeempty=false]  
        listreceivedbyaddress [minconf=1] [includeempty=false]  
        listsinceblock [blockhash] [target-confirmations]  
        listtransactions [account] [count=10] [from=0]  
        listunspent [minconf=1] [maxconf=9999999] ["address",...]  
        lockunspent unlock? [array-of-Objects]  
        move <fromaccount> <toaccount> <amount> [minconf=1] [comment]  
        sendfrom <fromaccount> <toCLcoinaddress> <amount> [minconf=1] [comment] [comment-to]  
        sendmany <fromaccount> {address:amount,...} [minconf=1] [comment]  
        sendrawtransaction <hex string> [allowhighfees=false]  
        sendtoaddress <CLcoinaddress> <amount> [comment] [comment-to]  
        setaccount <CLcoinaddress> <account>  
        setgenerate <generate> [genproclimit]  
        setmininput <amount>  
        settxfee <amount CLC/KB>  
        signmessage <CLcoinaddress> <message>  
        signrawtransaction <hex string> [{"txid":txid,"vout":n,"scriptPubKey":hex,"redeemScript":hex},...] [<privatekey1>,...] [sighashtype="ALL"]  
        stop  
        submitblock <hex data> [optional-params-obj]  
        validateaddress <CLcoinaddress>  
        verifychain [check level] [num blocks]  
        verifymessage <CLcoinaddress> <signature> <message>  

Additional Info
---------------
* When a call fails for any reason, it will return false and put the error message in `$client->error`

* The HTTP status code can be found in $client->status and will either be a valid HTTP status code or will be 0 if cURL was unable to connect.

* The full response (not usually needed) is stored in `$client->response` while the raw JSON is stored in `$client->raw_response`
