```python
# encoding=utf-8
import requests

# 这些是网址自己生成的
cookies = {
    'BIDUPSID': 'FC79E8CC7318E304E1FB8433953FD4DC',
    'PSTM': '1698729153',
    'BAIDUID': '719F2723712208A75191DD668BF235F8:FG=1',
    'newlogin': '1',
    'BAIDUID_BFESS': '719F2723712208A75191DD668BF235F8:FG=1',
    'ZFY': 'npUJYMp4aQmY136azzp:ABQBuTgli5e6nC:Beu7Gu6tpA:C',
    'MCITY': '-289%3A',
    'BDUSS': 'pmSGNiTGhNWmlhMXB5U3EzM1k3LU5NT35QQUo2Wk10bERTUUFlSncwQnR-bTltRUFBQUFBJCQAAAAAAAAAAAEAAACfnR1QYmFieb-txO4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAG1xSGZtcUhmT0',
    'BDUSS_BFESS': 'pmSGNiTGhNWmlhMXB5U3EzM1k3LU5NT35QQUo2Wk10bERTUUFlSncwQnR-bTltRUFBQUFBJCQAAAAAAAAAAAEAAACfnR1QYmFieb-txO4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAG1xSGZtcUhmT0',
    '__bid_n': '18b9f9875d69824a12a2ce',
    'H_PS_PSSID': '60269_60287_60298_60253',
    'H_WISE_SIDS': '60269_60287_60298_60253',
    'ET_WHITELIST': 'etwhitelistintwodays',
    'H_WISE_SIDS_BFESS': '60269_60287_60298_60253',
    'BA_HECTOR': 'ag8k0gahal8l2k010h2k8h85fd37dq1j5g3hg1u',
    'BDORZ': 'B490B5EBF6F3CD402E515D22BCDA1598',
    'BDRCVFR[feWj1Vr5u3D]': 'I67x6TjHwwYf0',
    'PSINO': '2',
    'delPer': '0',
    'ab_sr': '1.0.1_YzUwODllMDA0ZmFhNjU3ZWZkYjk2MmZmMzZjYjcwYzBhODJiZDRiYmMwYzkwMzdmMDA1MTdkMDg0YWIwMGI4NTlmZTk3YzZkYTNiNTI4MmZmNmFlMDcyN2UxNjgyYTRkZjc4NTk2NWIzYWJlZmRjYmFkODA5YjcwNjVlYTZkYzVjNzM3NDQzYTU0YmJhNzI0ZGYzM2M4YzQwNWU3YzllMQ==',
    'RT': '"z=1&dm=baidu.com&si=36809284-1fd7-4bb1-bc9d-62246b99282b&ss=lwr3mwpe&sl=1&tt=1qp&bcn=https%3A%2F%2Ffclog.baidu.com%2Flog%2Fweirwood%3Ftype%3Dperf&ld=1pycmb"',
}

headers = {
    'Accept': '*/*',
    'Accept-Language': 'en-US,en;q=0.9',
    'Connection': 'keep-alive',
    'Content-Type': 'application/x-www-form-urlencoded',
    # 'Cookie': 'BIDUPSID=FC79E8CC7318E304E1FB8433953FD4DC; PSTM=1698729153; BAIDUID=719F2723712208A75191DD668BF235F8:FG=1; newlogin=1; BAIDUID_BFESS=719F2723712208A75191DD668BF235F8:FG=1; ZFY=npUJYMp4aQmY136azzp:ABQBuTgli5e6nC:Beu7Gu6tpA:C; MCITY=-289%3A; BDUSS=pmSGNiTGhNWmlhMXB5U3EzM1k3LU5NT35QQUo2Wk10bERTUUFlSncwQnR-bTltRUFBQUFBJCQAAAAAAAAAAAEAAACfnR1QYmFieb-txO4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAG1xSGZtcUhmT0; BDUSS_BFESS=pmSGNiTGhNWmlhMXB5U3EzM1k3LU5NT35QQUo2Wk10bERTUUFlSncwQnR-bTltRUFBQUFBJCQAAAAAAAAAAAEAAACfnR1QYmFieb-txO4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAG1xSGZtcUhmT0; __bid_n=18b9f9875d69824a12a2ce; H_PS_PSSID=60269_60287_60298_60253; H_WISE_SIDS=60269_60287_60298_60253; ET_WHITELIST=etwhitelistintwodays; H_WISE_SIDS_BFESS=60269_60287_60298_60253; BA_HECTOR=ag8k0gahal8l2k010h2k8h85fd37dq1j5g3hg1u; BDORZ=B490B5EBF6F3CD402E515D22BCDA1598; BDRCVFR[feWj1Vr5u3D]=I67x6TjHwwYf0; PSINO=2; delPer=0; ab_sr=1.0.1_YzUwODllMDA0ZmFhNjU3ZWZkYjk2MmZmMzZjYjcwYzBhODJiZDRiYmMwYzkwMzdmMDA1MTdkMDg0YWIwMGI4NTlmZTk3YzZkYTNiNTI4MmZmNmFlMDcyN2UxNjgyYTRkZjc4NTk2NWIzYWJlZmRjYmFkODA5YjcwNjVlYTZkYzVjNzM3NDQzYTU0YmJhNzI0ZGYzM2M4YzQwNWU3YzllMQ==; RT="z=1&dm=baidu.com&si=36809284-1fd7-4bb1-bc9d-62246b99282b&ss=lwr3mwpe&sl=1&tt=1qp&bcn=https%3A%2F%2Ffclog.baidu.com%2Flog%2Fweirwood%3Ftype%3Dperf&ld=1pycmb"',
    'Origin': 'https://fanyi.baidu.com',
    'Referer': 'https://fanyi.baidu.com/mtpe-individual/multimodal?aldtype=16047&ext_channel=Aldtype',
    'Sec-Fetch-Dest': 'empty',
    'Sec-Fetch-Mode': 'cors',
    'Sec-Fetch-Site': 'same-origin',
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36',
    'sec-ch-ua': '"Google Chrome";v="125", "Chromium";v="125", "Not.A/Brand";v="24"',
    'sec-ch-ua-mobile': '?0',
    'sec-ch-ua-platform': '"Windows"',
}

# 这样开系统代理，就不会影响到爬虫
my_proxies = { 
    "http": None,
    "https": None
}

search_words = input("Please input the sentence or phrase you'd like to translate: ")

# post请求关键字
data = {
    'kw': search_words,
}

response = requests.post('https://fanyi.baidu.com/sug', cookies=cookies, headers=headers, data=data, proxies=my_proxies)
data = response.json().get("data")[0]  # 返回本身这个单词的意思，不做派生
print(data["v"])  # 输出意思
```

