---
wts:
    title: '22 - 복합 SLA 계산'
    module: '모듈 04 - Azure 과금과 지원'
---

# 22 - 복합 SLA 계산

이 연습에서는 서비스 SLA 가용성을 확인한 다음 응용프로그램의 복합 SLA 가용성을 계산합니다.

실습 시간: 15 분

예제의 응용프로그램은 다음과 같은 Azure 서비스로 구성됩니다. 우리는 세부적인 아키텍처 구성을 고려하지 않을 것이며, 여기서는 높은 수준의 예를 제공하는 것입니다.

+ **App service**: 응용프로그램 호스팅
+ **Azure AD B2C**: 사용자 로그인을 인증하고 프로필을 관리
+ **Application Gateway**: 응용프로그램 액세스와 스케일링을 관리
+ **Azure SQL Database**: 응용프로그램의 데이터 저장

# 실습 1: 응용 프로그램의 SLA 가용성 확인

1. 브라우저에서 <a href="https://azure.microsoft.com/ko-kr/support/legal/sla/summary/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure 서비스에 대한 SLA 요약</span></a> 웹페이지를 탐색합니다.

2. **App Service**의 SLA 가용성이 **99.95%**임을 확인합니다. **자세한 내용 보기**를 클릭하고 **SLA 세부정보**섹션을 확장하여 **월간 작동 시간 비율**과 **서비스 크레딧**을 확인합니다.

3. SLA 웹페이지로 돌아와서 **Azure Active Directory B2C**서비스의 가용성이 **99.9%**임을 확인합니다. 

4. **Azure Application Gateway**의 SLA 가용성은 **99.95%**입니다. 

5. Azure SQL database는 영역 중복 배포가 구성되지 않은 프리미엄 계층을 사용합니다.따라서 **Azure SQL Database**의 SLA 가용성은 **99.99%**입니다. 

    **메모**: Azure SQL Database의 구성 및 배포마다 다른 가용성을 갖습니다. 배포 및 구성을 계획하고 비용을 계산할 때 필요한 가동 시간을 명확히 하는 것이 중요합니다. 가동 시간의 작은 변화는 서비스 비용에 영향을 줄 뿐만 아니라 구성의 복잡성을 증가시킬 수 있습니다. Azure 서비스에 대한 SLA 요약 웹 페이지에서 예를 살펴볼만한 다른 서비스로는 **Virtual Machines**, **Storage Accounts**, **Cosmos DB**가 있습니다.

# 실습 2: 응용프로그램의 복합 SLA 가용성 계산

1. 응용프로그램을 구성하는 서비스를 사용할 수 없는 경우 사용자가 응용프로그램을 언활하게 사용할 수 없습니다. 따라서 응용프로그램의 총 가동 시간은 다음과 같이 구성됩니다.

    **App Service % 가용성** X **Azure AD B2C % 가용성** X  **Azure Application Gateway % 가용성** X **Azure SQL Database % 가용성** = **Total % 가용성**

    백분율로 표시하면 다음과 같습니다.

    **99.95%** X **99.9%** X **99.95%** X **99.99%** = **99.79%**


    현재의 서비스와 아키텍처로 응용프로그램이 달성할 수 있는 가동 시간의 백분율은 **99.79%**입니다.

샘플 응용프로그램의 각 서비스에 대한 SLA 가용성을 확인한 후 해당 응용프로그램에 대한 복합 SLA 가용성을 계산했습니다.
