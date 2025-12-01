# Jesync Pro Voucher Portal Template

A fully customizable and modern hotspot voucher portal designed for **Jesync Pro**.  
This template integrates seamlessly with **MikroTik Hotspot**, **DMA Radius**, and the **Jesync Voucher Store** backend to provide a smooth, automated voucher purchasing and login experience for ISP clients.

<p align="center">
  <img src="https://github.com/user-attachments/assets/96156a50-1733-4bfb-b0d9-473c061c5830" width="220" style="margin:8px;" />
  <img src="https://github.com/user-attachments/assets/e749095d-1fd8-481f-9f3b-dcbd141af56a" width="220" style="margin:8px;" />
  <img src="https://github.com/user-attachments/assets/502acb19-1599-4dc6-8b0c-6e089a35a21f" width="220" style="margin:8px;" />
</p>

---

## ✨ Features

### 🔐 Seamless MikroTik Hotspot Integration
- Automatic redirect from MikroTik Hotspot to the portal  
- Auto-login after voucher purchase  
- Built-in support for `/login`, `/logout`, and `/status` templates  
- Compatible with RouterOS v6 and v7

### 🎫 Smart Voucher Purchase Flow
- Full integration with **Jesync Voucher Store**
- Supports Xendit payment gateway (GCash, Maya, Cards, etc.)
- Automatic return to portal after successful purchase
- Auto-apply voucher code on redirect

### 📅 Real-Time Voucher Status
- Fetches voucher validity from DMA Radius / Jesync API  
- Displays validity days, expiry timestamp, remaining time  
- Live countdown timer (no refresh required)

### 🧩 Plug & Play Template System
- Customizable HTML, CSS, and JS  
- Works with all branded Jesync themes  
- Easy to embed your ISP logo and colors  
- Mobile-first responsive design

---

## 📁 Folder Structure

```
/hotspot
|- login.html
|- status.html
|- logout.html
|- js/
|- css/
|- images/
```

---

## 🚀 Quick Installation Guide

### **1. Upload Files to MikroTik Hotspot**
Upload the entire template folder to:

```
/ip hotspot profile set html-directory=hotspot
```

### **2. Redirect to Jesync Voucher Store**
Set your Mikrotik profile login & status page redirection:

```
http://<server-ip>:5000/voucher-store
```

### **3. Ensure Auto-Login Callback is Reachable**
Jesync backend auto-login URL must be accessible:

```
http://<server-ip>:5000/dma/auto-login
```

---

# 🔒 **Required: MikroTik Walled Garden Configuration (Single Script)**

Your hotspot users must be able to access all required external resources (styles, payment gateways, portals) **even without being logged in**.

Add this script to your MikroTik configuration:

```
/ip hotspot walled-garden
add comment="Jesync Pro Style CDN Rules" disabled=no
add comment=style dst-host=cdn.jsdelivr.net
add comment=style dst-host=fonts.googleapis.com
add comment=style dst-host=fonts.gstatic.com
add comment=style dst-host=use.fontawesome.com
add comment=style dst-host=cdnjs.cloudflare.com
/ip hotspot walled-garden ip
add action=accept comment="Jesync Pro Voucher Store" dst-address=172.16.100.4
add action=accept comment="Hotspot Gateway" dst-address=10.0.0.1
add action=accept comment=payments.gcash.com dst-host=payments.gcash.com
add action=accept comment=gcash-api.pulseid.com dst-host=gcash-api.pulseid.com
add action=accept comment=beacons.gcp.gvt2.com dst-host=beacons.gcp.gvt2.com
add action=accept comment=irisk-sea.alipay.com dst-host=irisk-sea.alipay.com
add action=accept comment=mss.paas.mynt.xyz dst-host=mss.paas.mynt.xyz
add action=accept comment=api.mynt.xyz dst-host=api.mynt.xyz
add action=accept comment=login.mynt.xyz dst-host=login.mynt.xyz
add action=accept comment=customer-segment-api.mynt.xyz dst-host=customer-segment-api.mynt.xyz
add action=accept comment=gw.alipayobjects.com dst-host=gw.alipayobjects.com
add action=accept comment=mdap.paas.mynt.xyz dst-host=mdap.paas.mynt.xyz
add action=accept comment=mgs-gw.paas.mynt.xyz dst-host=mgs-gw.paas.mynt.xyz
add action=accept comment=checkout.xendit.co dst-host=checkout.xendit.co
add action=accept comment=checkout-ui-gateway.xendit.co dst-host=checkout-ui-gateway.xendit.co
add action=accept comment=assets.xendit.co dst-host=assets.xendit.co
add action=accept comment=api.xendit.co dst-host=api.xendit.co
add action=accept comment=xqd9eal.x.incapdns.net dst-host=xqd9eal.x.incapdns.net
add action=accept comment=xen.to dst-host=xen.to
add action=accept comment=xnd-merchant-logos.s3.amazonaws.com dst-host=xnd-merchant-logos.s3.amazonaws.com
add action=accept comment=payments.paymaya.com dst-host=payments.paymaya.com
```

---

# 🧩 Customization

You can customize the portal with your own branding:

- Replace `/images/logo.png`
- Modify theme colors in `css/jesync.css`
- Update labels and UI text in `login.html`, `status.html`, and `voucher_success.html`

---

# 📞 Support

For assistance or custom integration:

**Jesync / JNHL IT Solutions**  
🌐 https://jesync.com  
📧 support@jesync.com  

---

# 📝 License

This template is provided as part of **Jesync Pro**.  
Redistribution or commercial use outside Jesync systems is not permitted.
