# 高併發 WordPress + WooCommerce 電商架構專案

本專案以 AWS 雲端服務架設一套具備高可用性、自動擴展與容錯機制的 WordPress + WooCommerce 電商平台，模擬「特價商品搶購」時的大量並發用戶存取，並導入壓力測試、備份、維運監控等完整解決方案。

---

## 🎯 專案目標

- 架設 WordPress + WooCommerce 電商平台
- 模擬高併發搶購情境，測試網站穩定性與可擴展性
- 建立具備以下特性的 AWS 架構：
  - 支援大量並發用戶
  - 可自動擴展的 EC2 群組
  - 高可用與容錯的流量負載平衡機制
  - 定期備份與災難復原規劃
  - 整合式系統監控與維運工具

---

## 🧱 架構設計概覽

- **Elastic Load Balancer (ALB)**  
  提供負載分流與高可用性，將流量分配至多個 EC2 實例。

- **EC2 Auto Scaling Group**  
  自動調整 EC2 數量以應對瞬間高流量需求，部署 WordPress 應用。

- **Amazon RDS (MySQL)**  
  提供穩定且可擴展的資料庫服務。

- **Amazon EFS**  
  跨多台 EC2 共享 WordPress 媒體與設定資料。

- **Amazon S3**  
  儲存 WooCommerce 靜態資源與備份檔案。

- **AWS Backup**  
  對 RDS、EFS 等資源進行自動化備份與災難復原。

- **AWS Systems Manager + CloudWatch**  
  提供即時監控、指令執行、自動修復與效能分析。

---

## ⚙️ 測試與模擬工具

- **Apache JMeter**
  - 模擬多位使用者同時搶購商品的高併發情境
  - 分析網站在不同流量條件下的反應時間與系統資源使用情況

---

## 🔒 安全性設計

- 所有服務皆部署於 **VPC 私有子網路**，透過 NAT Gateway 存取外部資源
- 利用 **Security Groups** 控制網路存取來源
- 實作 EC2 與 RDS 的 IAM 權限與憑證控管

---

## 📊 成果評估指標

- 同時併發用戶數與成功交易比例
- 自動擴展觸發次數與平均擴展時間
- 系統平均回應時間與 CPU/Memory 使用率
- CloudWatch Log 與 Dashboard 數據分析

---

## 📁 專案目錄架構

```plaintext
.
├── infra/             # Terraform 或 CloudFormation 腳本
├── wordpress/         # WordPress 設定與映像檔
├── jmeter/            # 壓力測試腳本與報告
├── docs/              # 架構圖、設計說明與操作文件
└── README.md          # 專案說明文件（本檔案）

