# **Steps to Create Azure Site-to-Site VPN**

## **Step 1: Prerequisites**
1. **On-Premises Network**:
   - VPN device capable of IPsec/IKE connectivity.
   - Azure-approved VPN device list: [Azure VPN Devices](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices).

2. **Azure Subscription**:
   - Ensure you have an active Azure subscription.

---

## **Step 2: Create a Virtual Network (VNet)**

# In Azure Portal:
1. Navigate to **Virtual Networks** → **+ Create**.
2. Configure:
   - Name: `MyVNet`
   - Address Space: `10.1.0.0/16`
   - Subnet: `10.1.0.0/24`
   - Region: Closest to on-premises network.
3. Click **Create**.

## **Step 3: Create a Gateway Subnet**

# In Azure Portal:
1. Go to **MyVNet** → **Subnets** → **+ Gateway Subnet**.
2. Configure:
   - Name: `GatewaySubnet`
   - Address range: `10.1.255.0/27`.
3. Click **Save**.

## **Step 4: Create a Virtual Network Gateway**

# In Azure Portal:
1. Navigate to **Virtual Network Gateways** → **+ Create**.
2. Configure:
   - Name: `MyVPNGateway`
   - Gateway Type: `VPN`
   - VPN Type: `Route-based`
   - SKU: `VpnGw1`
   - Virtual Network: `MyVNet`
   - Public IP: Create a new public IP (e.g., `MyVPNGatewayIP`).
3. Click **Review + Create**.
# Note: Deployment takes ~45 minutes.


## **Step 5: Configure the Local Network Gateway**

# In Azure Portal:
1. Navigate to **Local Network Gateways** → **+ Create**.
2. Configure:
   - Name: `MyLocalNetworkGateway`
   - IP Address: Public IP of the on-premises VPN device.
   - Address Space: `192.168.1.0/24` (on-premises CIDR block).
3. Click **Create**.

## **Step 6: Create a VPN Connection**

# In Azure Portal:
1. Navigate to **MyVPNGateway** → **Connections** → **+ Add**.
2. Configure:
   - Name: `MyVPNConnection`
   - Connection Type: `Site-to-Site (IPsec)`
   - Virtual Network Gateway: `MyVPNGateway`
   - Local Network Gateway: `MyLocalNetworkGateway`
   - Shared Key (PSK): `MySecretKey123`.
3. Click **OK**.

## **Step 7: Configure On-Premises VPN Device

# Steps:
1. Use the Azure-provided public IP address of the gateway.
2. Configure your VPN device with:
   - Remote Gateway IP: Azure Gateway Public IP.
   - Shared Key: `MySecretKey123`.
   - Local Subnet: On-premises network (e.g., `192.168.1.0/24`).
   - Remote Subnet: Azure VNet (`10.1.0.0/16`).
3. Refer to your VPN device documentation for configuration.

## **Step 8: Verify Connectivity

# In Azure Portal:
1. Go to **MyVPNConnection** → Check **Connection Status**.
2. Status should display: `Connected`.

# Test Connectivity:
1. Ping an Azure VM from your on-premises network or vice versa.



