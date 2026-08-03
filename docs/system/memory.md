# 診斷測試架構總覽 (H1 最大標題)
## 核心模組拆解 (H2 次標題)
### FCT 底層通訊機制 (H3 小標題)

```c
// 針對 TC3x 進行 UART 初始化設定
void Init_UART_Config(void) {
    IfxAsclin_Asc_Config ascConfig;
    IfxAsclin_Asc_initModuleConfig(&ascConfig, &MODULE_ASCLIN0);
    ascConfig.baudrate.baudrate = 115200;
    IfxAsclin_Asc_initModule(&g_ascHandle, &ascConfig);
}
```

```markdown
| 測項 ID | Amon 指令 | 自動化測試方法 | 狀態 (Risk) |
|---------|-----------|----------------|-------------|
| 2.1     | 2/1       | Basic_Hardware | 🟢 低風險   |
| 2.2.2   | 2/2/2/y   | Clear_CPU      | 🔴 高風險   |
| 2.16    | 2/16      | HW_Monitor     | 🟢 低風險   |
```

**測試環境建置步驟：**
1. 連接目標板 Serial 序列埠。
2. 開啟終端機並輸入驗證指令。
   * 確保波特率設定正確
   * 確認電源狀態