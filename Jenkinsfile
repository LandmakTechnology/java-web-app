pipeline {
    agent any
    stages {
        
        stage('Transition Jira Issue to IN PROGRESS') {
            steps {
                script {
                    sh '''#!/bin/bash

                    JIRA_URL="https://team4techsolutions.atlassian.net/"
                    JIRA_USERNAME="calson@team4techsolutions.com"
                    JIRA_API_TOKEN="ATATT3xFfGF0IsdAzJfFe2yEBJOu9NYEzRRNgVTr7lbeV2V2MAEUZYcgI029qRl-9ok5K9DTCXTnVIkx8bVJTc4fzwEvE21DcZqL7k0M-pKCoI_Uynsbwbmex_elUdbrfCuwy73M4Yv-w-_9njTUV25qFg0e7OqpMfpJOOafBOKobxdXS9VNtws=75C8017A"

                    # Extract the Jira issue key from the PR title
                    ISSUE_KEY=$(echo "$CHANGE_TITLE" | grep -oE 'DEV-[0-9]+')

                    # Fetch available transitions
                    TRANSITIONS_JSON=$(curl -s \
                        -H "Content-Type: application/json" \
                        -u "$JIRA_USERNAME:$JIRA_API_TOKEN" \
                        "${JIRA_URL}/rest/api/2/issue/$ISSUE_KEY/transitions")

                    echo "Available Transitions: $TRANSITIONS_JSON"

                    # Extract the ID for "IN PROGRESS"
                    TRANSITION_ID=$(echo "$TRANSITIONS_JSON" | jq '.transitions[] | select(.to.name | ascii_upcase == "IN PROGRESS") | .id' | tr -d '"')

                    # Logic to transition
                    if [ ! -z "$TRANSITION_ID" ]; then
                        TRANSITION_RESPONSE=$(curl -s -X POST \
                            -H "Content-Type: application/json" \
                            -u "$JIRA_USERNAME:$JIRA_API_TOKEN" \
                            -d '{
                                "transition": {
                                    "id": "'"$TRANSITION_ID"'"
                                }
                            }' \
                            "${JIRA_URL}/rest/api/2/issue/$ISSUE_KEY/transitions")
                        
                        echo "Transition Response: $TRANSITION_RESPONSE"
                    else
                        echo "The TRANSITION_ID is empty or not found."
                    fi
                    '''
                }
            }
        }
    }
}
