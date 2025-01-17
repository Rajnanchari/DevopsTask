# VPC Setup

## Step 1: Create VPC
- **Name**: `Demo-Vpc`
- **CIDR Block**: `10.0.0.0/16`

1. Go to the VPC Dashboard.
2. Click on **Create VPC**.
3. Enter `Demo-Vpc` as the VPC name.
4. Set the **CIDR Block** to `10.0.0.0/16`.
5. Click **Create**.

---

## Step 2: Create Internet Gateway

An Internet Gateway allows your VPC to connect to the internet, supporting both IPv4 and IPv6 traffic without introducing availability risks or bandwidth constraints.

### Instructions
1. Go to the **Internet Gateways** section.
2. Click on **Create Internet Gateway**.
3. Enter a name for the Internet Gateway (e.g., `IGW-Demo`).
4. Click **Create Internet Gateway**.

### Attach Internet Gateway to VPC
1. Select the created Internet Gateway.
2. Click on **Actions**.
3. Choose **Attach to VPC**.
4. Select `Demo-Vpc`.
5. Click **Attach**.

---

## Step 3: Create Subnets

Subnets are used to divide the VPC network into smaller segments, improving network efficiency.

### Instructions

#### Public Subnet
1. Go to the **Subnets** section.
2. Click on **Create Subnet**.
3. Select **VPC**: `Demo-Vpc`.
4. **Name**: `Pub-Subnet`.
5. **CIDR Block**: `10.0.0.0/20`.
6. Click **Create**.

#### Private Subnet
1. Go to the **Subnets** section.
2. Click on **Create Subnet**.
3. Select **VPC**: `Demo-Vpc`.
4. **Name**: `Pvt-Subnet`.
5. **CIDR Block**: `10.0.16.0/20`.
6. Click **Create**.

---

## Step 4: Create Route Tables

Route tables contain rules that dictate how network traffic is directed within your VPC.

### Instructions

#### Public Route Table
1. Go to the **Route Tables** section.
2. Click on **Create Route Table**.
3. **Name**: `Pub-Rt`.
4. Associate the subnet `Pub-Subnet` with `Pub-Rt`.
5. Add the following route:
   - **Destination**: `0.0.0.0/0`
   - **Target**: Attach to the Internet Gateway (IGW-Demo).

#### Private Route Table
1. Go to the **Route Tables** section.
2. Click on **Create Route Table**.
3. **Name**: `Pvt-Rt`.
4. Associate the subnet `Pvt-Subnet` with `Pvt-Rt`.
5. Leave the route as local only.

---

This setup will create a VPC with an Internet Gateway, one public subnet, one private subnet, and two route tables (public and private).
