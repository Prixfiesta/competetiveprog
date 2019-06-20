ll n;
vector<ll> adj[M];
ll subsz[2*M];
 
ll dfssub(ll u,ll p){
      
      ll ans = 1;
      for(auto it: adj[u]){
        if(it==p){
          continue;
        }
        ans+= dfssub(it,u);
      }
      return  subsz[u] = ans;
    }
    ll getcentroid(ll s){
      dfssub(s,-1);
      ll tot = subsz[s];
      ll f = 1;
    	ll  p = s;
      while(f){
      	// cout<<s<<"j\n";
        for(auto it : adj[s]){
          if(it!=p&&subsz[it]>tot/2){
            
            p=s;
            s = it;
            
            f=-1;
            break;
          }
          f=1;
        }
        if(f==1){
          return s;//should always get answer
        }
        f = 1;
      }
      //ainwayi hain 
      return s;
    }
