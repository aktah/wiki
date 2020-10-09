---
id: OnPlayerConnect
title: OnPlayerConnect
description: Callback นี้ถูกเรียกเมื่อผู้เล่นเชื่อมต่อกับเซิร์ฟเวอร์
tags: ["player"]
---

## คำอธิบาย

Callback นี้ถูกเรียกเมื่อผู้เล่นเชื่อมต่อกับเซิร์ฟเวอร์

| ชื่อ       | คำอธิบาย                          |
| -------- | ------------------------------------ |
| playerid | ไอดีของผู้เล่นที่เชื่อมต่อเข้ามา |

## ส่งคืน

1 - จะป้องกันไม่ให้ฟิลเตอร์สคริปต์อื่นถูกเรียกโดย Callback นี้

0 - บอกให้ Callback นี้ส่งต่อไปยังฟิลเตอร์สคริปต์ถัดไป

มันถูกเรียกในฟิลเตอร์สคริปต์ก่อนเสมอ

## ตัวอย่าง

```c
public OnPlayerConnect(playerid)
{
    new string[64], pName[MAX_PLAYER_NAME];
    GetPlayerName(playerid,pName,MAX_PLAYER_NAME);
    format(string,sizeof string,"%s ได้เชื่อมต่อเข้าไปยังเซิร์ฟเวอร์! ยินดีต้อนรับจ้า",pName);
    SendClientMessageToAll(0xFFFFFFAA,string);
    return 1;
}
```

## บันทึก

:::tip

NPC สามารถเรียก Callback นี้ได้

:::

## ฟังก์ชั่นที่เกี่ยวข้องกัน
