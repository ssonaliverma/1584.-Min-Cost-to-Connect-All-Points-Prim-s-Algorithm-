# 1584.-Min-Cost-to-Connect-All-Points-Prim-s-Algorithm-




int minCostConnectPoints(vector<vector<int>>& points) {
  

        int n=points.size();
        vector<pair<int,int>>adj[n];

        for(int i=0;i<n;i++)
        {
            vector<pair<int,int>>temp;
            for(int j=0;j<n;j++)
            {
                if(i!=j)
                {
                    int wt=abs(points[i][0]-points[j][0]) + abs(points[i][1]-points[j][1]);
                    adj[i].push_back({j,wt});
                }
            }
        }

        cout<<n;

        set<pair<int,int>>s;
        s.insert({0,0});//cost,node
        int ans=0;

        vector<int>vis(n+1,false);

        while(!s.empty())
        {
            pair<int,int>p=*(s.begin());

            s.erase(s.begin());

            if(!vis[p.second])
            {
               
                vis[p.second]=true;
                ans+=p.first;

                for(auto x : adj[p.second])
                {
                    // for(auto x : it)
                    // {
                        if(!vis[x.first])
                        {
                             
                            s.insert({x.second, x.first});
                        }
                   // }
                }
            }
        }

        return ans;
        
    }
