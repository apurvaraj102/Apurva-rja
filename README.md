#include <bits/stdc++.h>
using namespace std;

class Solution {
  public:
    
    vector<int> bfsOfGraph(int V, vector<int> adj[]) 
    {
        
        bool check[V];
        memset(check,false,sizeof(check));
        
        int s=0;
        
        check[s]=true;
        
        vector<int> ans;
        
        queue<int> q;
        q.push(s);
        
        while(!q.empty())
        {
            int t=q.front();
            ans.push_back(t);
            q.pop();
            
            for(int x:adj[t])
            {
                if(!check[x])
                {
                    check[x]=true;
                    q.push(x);
                }
            }
        }
        return ans;
    }
};


int main() {
    int tc;
    cin >> tc;
    while (tc--) {
        int V, E;
        cin >> V >>

            E;

        vector<int> adj[V];

        for (int i = 0; i < E; i++) {
            int u, v;
            cin >> u >> v;
            adj[u].push_back(v);
            // 		adj[v].push_back(u);
        }
        // string s1;
        // cin>>s1;
        Solution obj;
        vector<int> ans = obj.bfsOfGraph(V, adj);
        for (int i = 0; i < ans.size(); i++) {
            cout << ans[i] << " ";
        }
        cout << endl;
    }
    return 0;
} 
