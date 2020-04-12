---
layout: default
title: "[SW개발보안경진대회] A* 알고리즘을 이용한 안전길찾기 서비스"
date: 2020-02-16 10:00:00 +0900
published: 2020-02-13 10:00:00 +0900
comments: true
categories: development
tags: [contest, secure-coding, software, graph, map, a*, astar, shortest-path, algorithm, secure-coding, pedestrian-safety]
github: "https://github.com/PnDong/SafeDirection"
use_math: true
---

<p>
    현재는 다양한 길찾기 서비스가 있다. 하지만 이런 길찾기 서비스를 이용하는 사용자들은 가는 길에 어떤 위험요소가 있는지 확인하기 힘들고, 확인하더라도 대체 경로를 찾는 것이 쉽지 않다.
	공사중인 건물 붕괴 사고, 길거리 범죄, 차량 사고 등 많은 일들이 우리가 평소에 거니는 도로에서 일어난다.
	우리가 SW개발보안경진대회 해커톤에서 개발한 '안전길찾기'의 프로토타입은 이런 위험 요소들을 미리 확인하고,
	A* Search 알고리즘에 관한 정리를 이용해 완전하면서 안정적으로 최단 대체 경로, 즉 '안전한 길'을 찾는 방법을 제안한다.
</p>
<!--more-->

<h2>개요</h2>

<p>
	현재는 다양한 길찾기 서비스가 있다. 구글, 네이버 등 다양한 기업들이 출발지와 목적지를 입력하면 최단경로를 찾아주는 서비스를 운영하고 있다.
	한편, 공사중인 건물 붕괴 사고, 길거리 범죄, 차량 사고 등 많은 일들이 우리가 평소에 거니는 도로에서 일어난다. 하지만 이런 길찾기 서비스는 최단 경로를 찾는 것에 관심이 있고, '안전한' 경로를 찾는 것에는 큰 관심이 없다.
	따라서 기존의 길찾기 서비스를 이용하는 사용자들은 가는 길에 어떤 위험요소가 있는지 확인하기 힘들고, 알고 있더라도 다양하고 많은 위험요소를 고려해 대체 경로를 찾는 것이 쉽지 않다.
	우리가 2인 팀으로 출전해 SW개발보안경진대회 해커톤에서 개발한 '안전길찾기'의 프로토타입은 이런 위험 요소들을 미리 확인하고,
	A* Search 알고리즘에 관한 정리를 이용해 완전하면서 안정적으로 최단 대체 경로, 즉 '안전한 길'을 제안한다. 이 글에서는 이론적인 배경부터 어떤 API와 클라우드 서비스를 활용해서 개발했는지를 다룰 것이다.
	아이디어 및 알고리즘 부분에서는 안전길찾기의 핵심 아이디어를 다루고, 그래프로 표현된 지도에서
	유클리드 거리 외에 다양한 안전 속성을 가지고 있는 간선에 대해 A* Search 알고리즘이 안전을 고려한 최단 경로를 찾는 데 어떻게 완결성(completeness)과 최적성(optimality)을 가지는지 그 이론적 배경을 다룬다.
	구현 부분에서는 우리가 개발한 안전길찾기의 프로토타입이 어떤 플랫폼에서 어떤 API와 클라우드 서비스를 활용해서 어떻게 구현됐는지에 대해 다룬다.
</p>

<h2>아이디어 및 알고리즘</h2>

<h3>핵심 아이디어</h3>

<p>
	우선 지도를 다음과 같이 그래프로 표현하여 저장한다.
	<ul>
	<li>장소와 교차로는 노드로 나타낸다.</li>
	<li>노드 사이의 길이 존재하면, 실제 길의 길이와 길에 있는 안전/위험 요소를 속성으로 갖는 간선으로 나타낸다.</li>
	</ul>
	사용자가 출발지부터 목적지까지 이동하는 경로에 존재하는 안전요소들, 예를 들어 CCTV, 여성안전지킴이집, 길의 폭과 밝기, 24시 편의점, 그리고 안전위협요소들, 예를 들면 유흥가, 공사장소,
	철거단지 등에 대한 중요도를 사용자가 임의로 설정할 수 있는 변수로 둔다. 그 외에도 사용자들의 집단지성을 이용해 경로를 평가하여 이 또한 거리 산정에 고려될 수 있도록 한다.
	사용자가 출발지와 목적지를 입력하면, 이 서비스는 설정된 변수와 길의 속성을 기반으로 '안전 가중치'가 적용된 거리를 산정하고, 탐색 경우의 수를 효과적으로 줄인 A* 알고리즘을 이용해 안전을 고려한 최단 경로를 찾아 준다.
	편의를 위해서 안전 경로 제안 서비스는 거리상 최단 경로와 안전상 최단 경로 등을 같이 표시한다.
</p>

<h3>알고리즘</h3>

<p>
	A* Search 알고리즘은 다익스트라(Dijkstra) 알고리즘과 매우 유사하지만, 경로 비용 대신에 휴리스틱(heuristics)을 사용해 탐색 공간을 줄인다는 점에서 다익스트라 알고리즘과 차이가 있다. <br>

{% include pseudocode.html id="1" code="
\begin{algorithm}
\caption{Dijkstra's Algorithm}
\begin{algorithmic}
\PROCEDURE{Dijkstra}{$G, s, e$}
	\STATE initialize $cost[v], \forall v \in G(V)$
	\STATE initialize $predecessor[v], \forall v \in G(V)$
	\STATE create a vertex priority queue $Frontier$
	\STATE create a vertex set $Explored$
	\STATE $cost[s] \gets 0$
	\STATE $Frontier.add(s)$ with priority $cost[s]$
	\WHILE{$\neg Frontier.is$-$empty()$}
        \STATE $v \gets Frontier.extract$-$min()$
		\IF{$v = e$}
			\RETURN $construct$-$path(e)$
		\ENDIF
		\STATE add $v$ to $Explored$
        \FOR{$u \in N(v)$}
			\STATE $alt \gets cost[v]+w[u,v]$
			\IF{$u \notin Frontier \land u \notin Explored$}
				\STATE $Frontier.add(u)$ with priority $alt$
				\STATE $predecessor[u] \gets v$
			\ELIF{$u \in Frontier \land cost[u]>alt$}
				\STATE $Frontier.update$-$priority(u, alt)$
				\STATE $predecessor[u] \gets v$
			\ENDIF
		\ENDFOR
	\ENDWHILE
	\STATE $failed$ to find the shortest path
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
" %}

	위 다익스트라 최단 경로 탐색 알고리즘은 간선의 가중치로 정렬되는 우선순위 큐(priority queue)를 이용해 도달하는 데 드는 비용 $cost[n]$이 가장 작은 노드부터 탐색해나간다.
	A* 알고리즘은 다익스트라 알고리즘과 같이 우선순위 큐를 이용하지만,
	도달하는 데 드는 경로 비용 $cost[n]$이 아닌 경로 비용에 휴리스틱 함수의 값이 합쳐진 값, 즉 $f(n) = cost[n] + h(n)$이 가장 작은 노드부터 탐색해나간다.
	이를 직관적으로 이해해보자면, 노드 $n$을 판단할 때 노드 $n$에 도달하는 최소 비용 $cost[n]$은 이미 주어졌고, 노드 $n$에서 목적지 노드까지 가는 비용은 이론적인 최소값 $h(n)$으로 대충 정한 것이다.
	그래프 탐색에서 A* 알고리즘은 휴리스틱 $h(n)$이 다음과 같은 조건, 즉 일관성(consistency)을 갖출 때 완결성과 최적성을 모두 갖춘다.
	$$h(n) \leq c(n,n') + h(n')$$
	여기서 $c(n,n')$은 노드 $n$에서 노드 $n'$으로 가는 비용을 뜻한다.<br>
	위 수식은 삼각 부등식(triangle inequality)의 형태를 띠는데, 목적지까지의 유클리드 거리는 위 조건을 만족한다는 것을 쉽게 알 수 있다.
	따라서 노드가 장소, 간선이 장소간의 거리인 지도 그래프에서 목적지까지의 최단 경로를 찾는 데 A* 알고리즘은 효과적으로 탐색 공간을 줄일 수 있다.<br>
	다만 SafeDirection에서는 간선이 지도상 거리만을 가중치로 갖는 것이 아니라, 안전 요소와 안전 위협 요소에 대한 속성도 갖고 있다. 휴리스틱 $h(n)$으로는 그대로 유클리드 거리를 사용하면서,
	안전 요소와 안전 위협 요소를 거리 단위로 바꾸어 실제 지도상 거리에 더해주면 일관성 조건을 만족하게 되어 알고리즘이 완결성과 최적성을 가진다.
</p>

<h2>구현</h2>

<h3>그래프 XML 표현</h3>

<p>
	안전길찾기 프로토타입에 사용되는 더미 지도 데이터는 map_data.xml로 저장했으며, 구조는 대략 다음과 같다.
</p>

{% highlight xml %}
<?xml version="1.0" encoding="euc-kr"?>
<map>
	<nodeSet>
		<node id="1">
			<name>인화빌딩</name>
			<x>229</x>
			<y>115</y>
			<type />
		</node>
		<node id="2">
			<name>인화빌딩앞</name>
			<x>254</x>
			<y>115</y>
			<type />
		</node>
	</nodeSet>
	<edgeSet>
		<edge>
			<node id="1" />
			<node id="2" />
			<length>8</length>
			<width>12</width>
			<constructNum>0</constructNum>
			<adultEntNum>0</adultEntNum>
			<cctvNum>0</cctvNum>
			<convNum>1</convNum>
			<shelterNum>1</shelterNum>
			<brightness>1.0</brightness>
			<reputation />
		</edge>
	</edgeSet>
</map>
{% endhighlight %}

<h3>알고리즘 Java 구현</h3>

<p>
	안전길찾기에서 사용되는 A* 알고리즘은 다음과 같이 Java 코드로 구현하였다. MapGraph 클래스는 map_data.xml파일을 파싱하고, 지도 그래프의 노드와 간선을 관리하는 클래스이다.
</p>

{% highlight java %}
public List<MapGraph.MapVertex> AStarSearch(String startId, String endId, boolean safetyMode) {

    MapGraph.MapVertex startv = mg.findVertexById(startId);
    MapGraph.MapVertex endv = mg.findVertexById(endId);
    
    if(startv == null || endv == null)
    	return new ArrayList<>();
    
    mg.initCosts();
    mg.loadReputation();
    frontier.clear();
    explored.clear();
    
    startv.updateCost(0, mg.getDistance(startv, endv), null);
    frontier.add(startv);
    
    while(true) {
    	
    	if(frontier.isEmpty()) return null;
    	
    	MapGraph.MapVertex v = frontier.remove();
    	if(v.getId().equals(endId)) {
    		return mg.constructPath(endId);
    	}
    	explored.add(v.getId());
    	
    	for(MapGraph.MapVertex u : v.getNeighbors()) {
    		if(!frontier.contains(u) && !explored.contains(u.getId())) {
    			double cost;
    			if(safetyMode) {
    				cost = v.getCost() + mg.getEdgeCost(v, u) + mg.getSafetyCost(v, u);
    			}
    			else {
    				cost = v.getCost() + mg.getEdgeCost(v, u);
    			}
    			u.updateCost(cost, mg.getDistance(u, endv), v.getId());
    			frontier.add(u);
    		}
    		else if(frontier.contains(u) && u.getCost() > v.getCost() +  + mg.getSafetyCost(v, u) + mg.getEdgeCost(v, u)) {
    			frontier.remove(u);
    			double cost;
    			if(safetyMode) {
    				cost = v.getCost() + mg.getEdgeCost(v, u) + mg.getSafetyCost(v, u);
    			}
    			else {
    				cost = v.getCost() + mg.getEdgeCost(v, u);
    			}
    			u.updateCost(cost, mg.getDistance(u, endv), v.getId());
    			frontier.add(u);
    		}
    	}
    }
}
{% endhighlight %}

<p>
	길의 안전/위험 요소들을 거리 단위로 바꿔주는 MapGraph 클래스의 getSafetyCost(v,u)메소드는 다음과 같이 정의된다. 단위 변환 규칙은 이후 인터페이스 설명하는 부분에 나온다.
</p>

{% highlight java %}
public double getSafetyCost(MapVertex v, MapVertex u) {
	MapEdge e = getEdge(v, u);
	if (e != null) {
		double reputation;
		if (v.getId().compareTo(u.getId()) > 0)
			reputation = getAverageReputation(u.getId(), v.getId());
		else
			reputation = getAverageReputation(v.getId(), u.getId());
		return Settings.getReputationImp() * (5 - reputation)
				+ Settings.getCctvImp() * ((e.length - e.cctvNum * 20) > 0 ? (e.length - e.cctvNum * 20) : 0) * 0.5
				+ Settings.getShelterImp()
						* ((e.length - e.shelterNum * 50) > 0 ? (e.length - e.shelterNum * 50) : 0) * 0.5
				+ Settings.getConvenienceImp()
						* ((e.length - e.convenienceNum * 50) > 0 ? (e.length - e.convenienceNum * 50) : 0) * 0.5
				+ Settings.getWidthImp() * (e.averageWidth > 10 ? 0 : (10 - e.averageWidth)) * e.length * 0.01
				+ Settings.getBrightnessImp() * (1 - e.averageBrightness) * e.length * 0.02
				+ Settings.getAdultEntImp() * e.adultEntNum + Settings.getConstructionImp() * e.constructionNum * 2;
	}
	return 0;
}
{% endhighlight %}

<h3>데이터베이스 및 인터페이스 구축</h3>

<p>
	대회 주최측에서 Microsoft Azure 클라우드 서비스를 이용할 수 있는 5만원 제한의 Microsoft Azure Pass를 제공해주었고, 이를 이용해 가상머신을 호스팅하고 데이터베이스 서버를 구축했다.
</p>

<a href="/assets/images/{{page.id}}/azure.png"> <img width="200" height="58"
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/azure.png" alt="Logo of Azure"/></a>

<p>
	데이터베이스 관리 시스템(DBMS)으로는 관계형 데이터베이스 관리 시스템인 MySQL을 사용했다. 데이터베이스 서버에는 사용자 정보와, 길에 대한 평가 정보가 저장되어 있다.
</p>

<a href="/assets/images/{{page.id}}/mysql.png"> <img
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/mysql.png" alt="Logo of MySQL"/></a>

<p>
	인터페이스는 Java로 구현했으며, GUI는 Swing, 데이터베이스 접속은 JDBC, XML을 파싱은 XPath API로 구현했다. 다음은 구현된 인터페이스의 스크린샷 몇 장이다.
	마지막 스크린샷에서 안전거리 변환 방식을 확인할 수 있다.
</p>


<a href="/assets/images/{{page.id}}/screenshot1.png"> <img
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/screenshot1.png" alt="screenshot1"/></a>
<p align="center">로그인 UI.</p>

<a href="/assets/images/{{page.id}}/screenshot2.png"> <img
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/screenshot2.png" alt="screenshot2"/></a>
<p align="center">지도 UI. 안전/위험 요소들은 각각 색상이 다른 원으로 표시했다.</p>

<a href="/assets/images/{{page.id}}/screenshot3.png"> <img
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/screenshot3.png" alt="screenshot3"/></a>
<p align="center">길찾기를 실행한 모습. 빨간색 실선이 최단 경로, 파란색 실선이 안전을 고려한 최단 경로이다.</p>

<a href="/assets/images/{{page.id}}/screenshot4.png"> <img
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/screenshot4.png" alt="screenshot4"/></a>
<p align="center">길 안전 평가 UI. 길에 대한 안전도 평가를 내릴 수 있다.</p>

<a href="/assets/images/{{page.id}}/screenshot5.png"> <img
	class="center-block img-responsive"
	src="/assets/images/{{page.id}}/screenshot5.png" alt="screenshot5"/></a>
<p align="center">중요도 설정 UI. 안전거리에 대한 기준을 확인할 수 있다.</p>

<p>
	우리 팀은 안전길찾기 프로토타입의 최종 발표를 마치고, 한국정보보호학회장상과 스패로우상, 총 두 개의 상을 수상하며 대회를 성공적으로 마쳤다.
</p>

	
<h2>결론 및 느낀점</h2>

<p>
	안전/위험 요소가 포함된 지도 그래프에 대한 A* 알고리즘은 매우 안정적으로 돌아갔다. 안전/위험 요소들을 거리 단위로 바꾸는 것에서 시행착오를 많이 거쳤지만,
	나름대로 합리적인 변환을 찾고, 사용자가 커스터마이징 할 수 있는 형태로 만들어 잘 해결한 것 같다.<br>
	다만 프로토타입은 더미 데이터로 제작했고, 실제 서비스로 제공할 것을 생각하면 사용자 인증 절차를 추가하고 외관이나 범용성을 고려해 고쳐야할 것 같다.
	또, 집단지성을 이용해 등록되지 않은 안전/위험 요소를 추가하는 것도 고려해볼 만한 것 같다.
	여유가 된다면 휴대폰 인증과 등록 기능을 추가하고 행안부 등의 지도 API를 이용해서 웹 사이트나 모바일 앱으로 구현을 해서 서비스를 하고 싶다.<br>
	대학교에 입학하고 처음 시도한 대회였다. 서비스 개발 경험이 거의 없는 나와 내 팀원으로서는 매우 큰 도전이었고, 힘든 순간도 많았다.
	하지만 다른 팀의 능력있는 개발자들을 보면서, 내 부족한 부분과 자신있는 부분에 대해 많이 알게 됐다. 앞으로는 더 자신감 있는 도전을 할 수 있을 것이다.<br>
</p>
